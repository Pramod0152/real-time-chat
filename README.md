# Chat Application

A real-time chat application that allows users to communicate through instant messaging. Messages are processed asynchronously using a queue-based architecture to improve scalability and performance under high concurrency.

## How it works

1. **Authentication:** users authenticate through JWT, and Socket.IO connections are verified before joining chat rooms.
2. **Real-time communication:** the NestJS Socket.IO gateway handles incoming messages and manages room-based communication.
3. **Message processing:** incoming messages are pushed into a Redis queue using BullMQ, allowing the gateway to handle requests without waiting for database operations.
4. **Background processing:** worker processes consume queued messages, persist them in PostgreSQL using Sequelize, and trigger Firebase push notifications when needed.
5. **Event broadcasting:** processed messages are broadcast to the appropriate Socket.IO rooms, allowing connected users to receive messages in real time.
6. **Client-side synchronization:** Zustand and TanStack Query manage client-side state and cache updates as new messages arrive.

## Repositories

| **Service** | **Repo** | **Stack** | **Role** |
| ----------- | -------- | --------- | -------- |
| API | [chat-api](https://github.com/Pramod0152/chat-api) | NestJS, TypeScript, Socket.IO, Redis, BullMQ, PostgreSQL | Authentication, real-time communication, message processing, and notifications |
| Web | [chat-app](https://github.com/Pramod0152/chat-app) | React, TypeScript, Zustand, TanStack Query | Chat interface and real-time client-side synchronization |
