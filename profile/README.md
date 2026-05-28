# 📸 Instagram Clone - Microservices Backend

A comprehensive backend service simulating a modern social media platform like Instagram. Built with a distributed microservices architecture, it exposes REST APIs to manage users, followers, posts, multimedia uploads, real-time chat, and async notifications.

![Java](https://img.shields.io/badge/Java_21-orange?style=flat&logo=openjdk&logoColor=white)
![Spring Boot](https://img.shields.io/badge/Spring_Boot_4-6DB33F?style=flat&logo=springboot&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-316192?style=flat&logo=postgresql&logoColor=white)
![Neo4J](https://img.shields.io/badge/Neo4J-008CC1?style=flat&logo=neo4j&logoColor=white)
![Kafka](https://img.shields.io/badge/Kafka-231F20?style=flat&logo=apachekafka&logoColor=white)
![JWT](https://img.shields.io/badge/JWT-black?style=flat&logo=jsonwebtokens&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat&logo=docker&logoColor=white)
![Kubernetes](https://img.shields.io/badge/Kubernetes-326CE5?style=flat&logo=kubernetes&logoColor=white)
![Cloudinary](https://img.shields.io/badge/Cloudinary-3448C5?style=flat&logo=cloudinary&logoColor=white)
![GKE](https://img.shields.io/badge/GKE-4285F4?style=flat&logo=googlecloud&logoColor=white)

<br/>

[![Scalar API Portal](https://img.shields.io/badge/Run_in-Scalar_API_Portal-E1306C?style=for-the-badge&logo=instagram&logoColor=white)](http://8.233.191.128/reference.html#)

[![Postman Collection](https://img.shields.io/badge/Postman-Collection-FF6C37?style=for-the-badge&logo=postman&logoColor=white)](https://documenter.getpostman.com/view/placeholder-collection-link)

---

## 🧩 Features

### User & Auth
- Register and login with secure JWT authentication
- Manage public or private account status
- Update profile details and profile picture

### Social Graph (Followers)
- Direct follow for public accounts
- Send, accept, or reject follow requests for private accounts
- View follower and following lists

### Posts & Media
- Upload multimedia assets securely (images/videos)
- Create posts with captions
- Like posts and view paginated feed

### Real-Time Chat
- Send private messages to other users
- Persist chat history efficiently

### Notifications (Event-Driven)
- Asynchronous fan-out notifications powered by Kafka
- Get notified when someone follows you, likes your post, or when someone you follow creates a new post.

---

## 📡 API Reference

> All protected endpoints require `Authorization: Bearer <accessToken>` in the request header.

### User & Auth Service (`/auth` & `/users`)
| Method | Endpoint | Auth | Description |
|--------|----------|------|-------------|
| ![POST](https://img.shields.io/badge/POST-blue?style=flat) | `/auth/signup` | Public | Register a new user account |
| ![POST](https://img.shields.io/badge/POST-blue?style=flat) | `/auth/login` | Public | Login and receive access tokens |
| ![GET](https://img.shields.io/badge/GET-brightgreen?style=flat) | `/users/me` | Bearer | Get the logged-in user's profile |
| ![PATCH](https://img.shields.io/badge/PATCH-orange?style=flat) | `/users/me` | Bearer | Update profile details (username, name, bio, privacy status) |
| ![POST](https://img.shields.io/badge/POST-blue?style=flat) | `/users/me/profile-picture` | Bearer | Upload and update profile picture |
| ![GET](https://img.shields.io/badge/GET-brightgreen?style=flat) | `/users/{username}` | Bearer | View another user's public profile |

### Follow Service (`/follow`)
| Method | Endpoint | Auth | Description |
|--------|----------|------|-------------|
| ![POST](https://img.shields.io/badge/POST-blue?style=flat) | `/follow/{userId}` | Bearer | Follow a public account directly |
| ![DELETE](https://img.shields.io/badge/DELETE-red?style=flat) | `/follow/{userId}` | Bearer | Unfollow a user |
| ![POST](https://img.shields.io/badge/POST-blue?style=flat) | `/follow/request/{userId}` | Bearer | Send a follow request to a private account |
| ![POST](https://img.shields.io/badge/POST-blue?style=flat) | `/follow/request/{userId}/accept` | Bearer | Accept an incoming follow request |
| ![GET](https://img.shields.io/badge/GET-brightgreen?style=flat) | `/follow/{userId}/followers` | Bearer | Get a user's followers list |
| ![GET](https://img.shields.io/badge/GET-brightgreen?style=flat) | `/follow/{userId}/following` | Bearer | Get a user's following list |

### Post Service (`/posts`)
| Method | Endpoint | Auth | Description |
|--------|----------|------|-------------|
| ![POST](https://img.shields.io/badge/POST-blue?style=flat) | `/posts` | Bearer | Create a new post with images |
| ![GET](https://img.shields.io/badge/GET-brightgreen?style=flat) | `/posts/{postId}` | Bearer | Get post details by ID |
| ![POST](https://img.shields.io/badge/POST-blue?style=flat) | `/posts/{postId}/like` | Bearer | Like a post |
| ![GET](https://img.shields.io/badge/GET-brightgreen?style=flat) | `/posts/feed` | Bearer | View paginated feed of posts from followed users |

### Chat Service (`/chat`)
| Method | Endpoint | Auth | Description |
|--------|----------|------|-------------|
| ![POST](https://img.shields.io/badge/POST-blue?style=flat) | `/chat/send` | Bearer | Send a real-time message to another user |
| ![GET](https://img.shields.io/badge/GET-brightgreen?style=flat) | `/chat/history/{userId}` | Bearer | Retrieve message history with a specific user |

### Notification Service (`/notifications`)
| Method | Endpoint | Auth | Description |
|--------|----------|------|-------------|
| ![GET](https://img.shields.io/badge/GET-brightgreen?style=flat) | `/notifications/me` | Bearer | View logged-in user's notification feed |
| ![PATCH](https://img.shields.io/badge/PATCH-orange?style=flat) | `/notifications/me/read` | Bearer | Mark specific notifications as read |
| ![DELETE](https://img.shields.io/badge/DELETE-red?style=flat) | `/notifications/me/{notificationId}` | Bearer | Delete a specific notification |

---
