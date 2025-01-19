# Kahunas Coaching Platform

A comprehensive coaching platform built with a microservices architecture, consisting of an AI-powered fitness trainer bot, coaching management API, and an admin dashboard.

## System Architecture

The platform consists of three main services:

- **AI Fitness Bot** (Port 3000): NestJS-based chatbot providing personalized fitness advice
- **Admin Dashboard** (Port 3001): Next.js application for platform management
- **Coaching API** (Port 3002): NestJS-based API handling core business logic

## Services Overview

### AI Fitness Bot
- AI-powered fitness and nutrition advice
- Response quality evaluation system
- Usage statistics and analytics
- Accessible at `http://localhost:3000`

### Admin Dashboard
- Client management interface
- Analytics dashboard
- AI response statistics
- Accessible at `http://localhost:3001`

### Coaching API
- User and session management
- Analytics and reporting
- Role-based access control
- Accessible at `http://localhost:3002`

## Prerequisites

- Docker and Docker Compose
- Node.js (v18 or higher)
- MySQL 8.0

## Environment Variables

Create a `.env` file in the root directory with:

```env
JWT_SECRET=your_jwt_secret
MYSQL_USER=kahunas_user
MYSQL_PASSWORD=mysecurepass123
```

## Getting Started

1. Clone the repository:
```bash
git clone <repository-url>
cd kahunas
```

2. Start the services:
```bash
docker-compose up -d
```

This will start:
- Two MySQL databases (kahunas-db on port 3306, ai-bot-db on port 3307)
- AI Bot service on port 3000
- Admin Dashboard on port 3001
- Coaching API on port 3002

## Database Structure

The system uses two separate MySQL databases:

### Kahunas DB (Port 3306)
- Main application database
- Stores user data, sessions, and coaching information

### AI Bot DB (Port 3307)
- Stores AI interaction data
- Manages response quality metrics and usage statistics

## Network Configuration

All services communicate through a Docker bridge network named `app-network`. The services are configured to work together seamlessly with the following dependencies:

- Admin Dashboard → Coaching API
- Admin Dashboard → AI Bot
- AI Bot → Coaching API

## Development

Each service can be developed independently. Refer to the individual service READMEs for specific development instructions:

- [AI Bot README](./ai-bot/README.md)
- [Coaching API README](./kahunas-api/README.md)
- [Admin Dashboard README](./kahunas-admin-dashboard/README.md)

## Production Deployment

The services are deployed on AWS EC2 instances:

- AI Bot: http://3.110.156.167:80
- Coaching API: http://13.127.188.120:80
- Admin Dashboard: http://13.233.45.0/login

## Monitoring

All services are monitored using AWS CloudWatch for:
- Performance metrics
- Error logging
- Resource utilization

## Tech Stack

- **Frontend**: Next.js, React, Tailwind CSS
- **Backend**: NestJS, TypeORM
- **Databases**: MySQL 8.0
- **AI Integration**: OpenAI GPT-3.5
- **Authentication**: JWT
- **Infrastructure**: Docker, AWS EC2, CloudWatch
