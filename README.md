# Coding Game Platform 

## Project Overview

This project is a gamified coding platform where users learn programming by solving challenges and progressing through levels and worlds.

Users start as beginners and grow step by step until advanced level through a structured learning path, similar to a game.

The platform combines:

- Learning
- Competition
- Gamification
- Professional system design

This is both a school project and a portfolio-level application.

---

## Vision

Build an online coding game where users progress from beginner to advanced through structured challenges, earn XP, unlock levels, and compete in rankings.

The goal is to make learning programming fun, motivating, and serious.

---

## Target Users

### Main Users
- Students
- Beginner programmers
- Self-learners
- Anyone who wants to practice coding

### Admins (Internal Only)
- Platform managers (project team)
- Manage content and moderation

Teachers are not required users.

---

## Core Concept: “From Zero to Hero”

Users follow a learning journey represented as a map:
Beginner → Explorer → Coder → Warrior → Hero → Legend

Each level contains challenges. Users unlock new levels by solving problems. Progress is visual and motivating.

---

## Game Structure (Worlds & Levels)

The platform is divided into Worlds, each focusing on specific skills.

### Example Worlds

**World 1 — Basics**
- Variables
- Conditions
- Loops

**World 2 — Arrays & Strings**
- Searching
- Sorting
- Parsing

**World 3 — Algorithms**
- Recursion
- Greedy
- Dynamic Programming

**World 4 — Data Structures**
- Stack
- Queue
- Trees
- Graphs

**World 5 — Master**
- Mixed problems
- Optimization
- Real scenarios

Each world contains normal challenges and one “Boss” challenge. Boss problems unlock the next world.

---

## Main Features

1. **User System**
   - Register / Login
   - Secure authentication
   - User profile
   - Password encryption

2. **Problem System**
   - Title, Description, Examples, Constraints, Difficulty
   - Public and hidden test cases

3. **Coding & Submission**
   - Online code editor
   - Language selection
   - Submit code
   - Automatic evaluation
   - Status feedback: Accepted, Wrong Answer, Time Limit, Runtime Error

4. **Learning Feedback**
   - Execution result
   - Failed test info (partial)
   - Retry option
   - Submission history
   - Optional hints

5. **XP & Level System**
   Users earn XP by solving problems. Example:

| Action | XP |
|--------|----|
| Easy | +10 |
| Medium | +25 |
| Hard | +50 |
| Boss | +100 |
| First Try Bonus | +10 |

Level is calculated from total XP and unlocks new worlds.

6. **Ranking & Competition**
   - Global leaderboard
   - World-based ranking
   - User rank
   - Score tracking

7. **Profile System**
   - Level
   - XP
   - Solved problems
   - Success rate
   - Badges
   - Rank

8. **Admin System**
   Hidden admin panel for:
   - Creating problems
   - Managing test cases
   - Managing users
   - Moderation
   - Viewing statistics

---

## User Journey

**New User**
1. Creates account
2. Enters World 1
3. Solves first problem
4. Gains XP
5. Unlocks next level

**Regular User**
1. Logs in
2. Checks leaderboard
3. Solves challenges
4. Levels up
5. Competes with others

**Admin**
1. Logs in
2. Manages content
3. Monitors system
4. Updates challenges

---

## System Modules

The platform is divided into six main modules:

Authentication Module

User Management Module

Problem Management Module

Submission & Judge Module

Ranking & XP Module

Admin Dashboard


---

## Technical Stack

**Backend**
- Jakarta EE (JEE)
- JAX-RS (REST API)
- JPA (Hibernate)
- JWT Authentication
- CDI / EJB

**Application Server**
- Tomcat

**Database**
- PostgreSQL (preferred) / MySQL

**Judge System**
- Docker containers
- Isolated execution
- Time & memory limits
- Separate execution service

**Frontend**
- React (Web application)

**Infrastructure**
- Nginx (optional)
- Linux server
- GitHub for version control

---

## Security Principles

- Password hashing (BCrypt)
- JWT tokens
- Isolated code execution
- No user code inside main server
- Role-based access (USER / ADMIN)

---

## Submission Workflow
User submits

Backend saves submission

Backend sends to Judge

Judge runs code in Docker

Judge returns result

Backend updates database

XP and rank updated


---

## Development Roadmap

**Phase 1 — Foundation (2 Weeks)**
- Project setup
- Database schema
- Authentication
- Basic API
- User system

**Phase 2 — Core System (3 Weeks)**
- Problem management
- Submission system
- Judge integration
- Basic XP system

**Phase 3 — Game Features (2 Weeks)**
- Worlds & levels
- Leaderboards
- Profiles
- Badges
- Admin panel

**Phase 4 — Polish (1–2 Weeks)**
- UI improvements
- Performance optimization
- Logging
- Documentation
- Security review

---

## Team Organization (2 Members)

**Member A — System Lead**
- Backend logic
- Database
- XP system
- Submission pipeline
- Judge integration
- Security

**Member B — UX Lead**
- Frontend UI
- Map design
- User experience
- Profiles
- Leaderboards
- Animations

---

## Project Strength (Portfolio Value)

This project demonstrates:

- Backend architecture
- Distributed systems
- Secure execution
- Database design
- DevOps basics
- System thinking
- Product design

---

## Project Philosophy

- Quality over quantity
- Clean architecture
- Real-world standards
- No shortcuts
- Professional documentation

---

## One-Sentence Description

A gamified coding platform where users progress through worlds and levels, solve programming challenges, earn XP, and grow from beginner to advanced developer.


