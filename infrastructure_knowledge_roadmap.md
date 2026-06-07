# Infrastructure Knowledge Roadmap

A step-by-step learning path to understand how a web application moves from code on a laptop to a real production system used by users.

---

## 1. Web Application Basics

A web application is usually made of:

```text
User
 ↓
Browser / Mobile App
 ↓
Frontend
 ↓
Backend API
 ↓
Database
 ↓
Storage / Cache / Queue / External Services
```

Example:

```text
classintown.com
 ↓
Angular website
 ↓
Node.js / Express APIs
 ↓
MongoDB
 ↓
Emails, WhatsApp, Google Calendar, Payments, Notifications
```

You should understand:

- What happens when a user opens a website?
- What is a browser request?
- What are HTML, CSS, and JavaScript?
- What is an API?
- What is a server?
- What is a database?

---

## 2. Frontend, Backend, Database

This is the core foundation.

```text
Frontend = What the user sees
Backend = Business logic
Database = Permanent data storage
```

Example:

```text
Frontend:
- Login page
- Class listing page
- Payment page
- Instructor dashboard

Backend:
- Login API
- Create class API
- Enrollment API
- Payment verification API

Database:
- Users
- Classes
- Enrollments
- Payments
- Notifications
```

For a MEAN stack application:

```text
MongoDB  → Database
Express  → Backend API framework
Angular  → Frontend
Node.js  → Backend runtime
```

---

## 3. Request–Response Flow

You must understand how one user action works end to end.

Example: user logs in.

```text
User enters mobile/email
 ↓
Angular sends request
 ↓
Node.js API receives request
 ↓
Backend validates data
 ↓
Backend checks MongoDB
 ↓
Backend creates token
 ↓
Response goes back to Angular
 ↓
User enters dashboard
```

Important topics:

- HTTP
- HTTPS
- GET
- POST
- PUT
- PATCH
- DELETE
- Status codes
- Headers
- Request body
- Response body
- Cookies
- Tokens

---

## 4. APIs

APIs connect the frontend and backend.

Example API routes:

```text
POST /api/v1/auth/login
GET /api/v1/classes
POST /api/v1/enrollments
PATCH /api/v1/payments/:id
```

You should learn:

- REST APIs
- API versioning
- Request validation
- Response structure
- Error handling
- Authentication middleware
- Authorization middleware
- Rate limiting

Good API response format:

```json
{
  "success": true,
  "message": "Login successful",
  "data": {}
}
```

Good error response format:

```json
{
  "success": false,
  "errorType": "VALIDATION_ERROR",
  "message": "Mobile number is required"
}
```

---

## 5. Authentication and Authorization

Authentication means:

```text
Who are you?
```

Authorization means:

```text
What are you allowed to do?
```

Example:

```text
Student can enroll in a class.
Instructor can approve enrollment.
Admin can manage users.
Super admin can manage platform settings.
```

Learn:

- JWT token
- Refresh token
- Session
- Password hashing
- OTP login
- Google login
- Role-based access control
- Permission-based access control

---

## 6. Database Design

This is extremely important.

For MongoDB, learn:

- Collections
- Documents
- References
- Embedded documents
- Indexes
- Aggregation
- Transactions
- Schema design

Example collections:

```text
User
Class
Schedule
Enrollment
PaymentPlan
Payment
Notification
ChatMessage
```

You must understand:

- When to embed data
- When to reference data
- How to avoid duplicate data
- How to design indexes
- How to handle soft delete
- How to track `createdAt` and `updatedAt`

---

## 7. File Storage

Most real applications need file uploads.

Examples:

- Profile image
- Class image
- Payment proof
- QR code
- Documents
- Certificates

Learn:

- Multer
- Local file storage
- Public folder
- Private file storage
- S3 bucket
- CloudFront/CDN
- File size limits
- File type validation
- Signed URLs

Basic flow:

```text
User uploads file
 ↓
Backend validates file
 ↓
File is stored in server/S3
 ↓
File URL is saved in database
 ↓
Frontend displays file
```

---

## 8. Emails, SMS, WhatsApp, Push Notifications

Real applications communicate with users.

Learn:

- Email service
- SMS service
- WhatsApp Business API
- Web push notifications
- Firebase FCM for mobile
- In-app notifications
- Socket notifications

Example:

```text
Student enrolls
 ↓
Instructor gets notification
 ↓
Email sent
 ↓
WhatsApp sent
 ↓
Push notification sent
 ↓
Notice saved in database
```

---

## 9. Real-Time Communication

Used for chat, live notifications, and dashboards.

Learn:

- WebSocket
- Socket.IO
- Rooms
- Events
- Online users
- Unread count
- Real-time updates

Example:

```text
Student sends message
 ↓
Backend receives socket event
 ↓
Message saved in database
 ↓
Instructor receives message instantly
```

---

## 10. Server Basics

Now move from code to infrastructure.

Learn:

- What is a server?
- What is Linux?
- What is Ubuntu?
- What is SSH?
- What is a process?
- What is a port?
- What is a firewall?

Basic server flow:

```text
Developer laptop
 ↓
GitHub
 ↓
Server
 ↓
Application runs on port 3000
 ↓
Nginx exposes it to the internet
```

Commands to know:

```bash
ssh user@server-ip
ls
cd
mkdir
nano
cat
tail
ps
kill
sudo
chmod
chown
```

---

## 11. Node.js App Deployment

For a Node.js backend, learn:

- `npm install`
- Environment variables
- `.env` files
- PM2
- Logs
- Restart
- Reload
- Build

Typical backend deployment:

```bash
git pull
npm install
npm run build
pm2 restart app
pm2 logs
```

PM2 concepts:

- Process manager
- Auto restart
- Logs
- Startup script
- Cluster mode
- Environment config

---

## 12. Frontend Deployment

Angular app deployment flow:

```text
Angular source code
 ↓
npm run build
 ↓
dist folder generated
 ↓
Nginx serves static files
 ↓
Browser loads Angular app
```

Learn:

- Angular build
- Environment files
- API base URL
- Static hosting
- Browser caching
- Service worker
- SPA routing fallback

Important Nginx setting for Angular:

```text
All frontend routes should fallback to index.html
```

---

## 13. Nginx and Reverse Proxy

Nginx is a very important infrastructure component.

It can:

- Serve frontend
- Forward API requests to Node.js
- Handle HTTPS
- Handle redirects
- Compress files
- Set upload limits
- Route WebSocket traffic

Typical flow:

```text
User visits classintown.com
 ↓
Nginx receives request on port 443
 ↓
If frontend route → serve Angular
 ↓
If /api route → forward to Node.js port 3000
 ↓
If /socket.io route → forward WebSocket
```

---

## 14. Domain, DNS, SSL

This is where your app becomes public.

Learn:

- Domain name
- DNS
- A record
- CNAME
- Nameserver
- SSL certificate
- HTTPS
- Let's Encrypt
- Certbot

Example:

```text
classintown.com
 ↓
DNS A record points to server IP
 ↓
Nginx receives request
 ↓
SSL certificate secures connection
 ↓
App loads securely
```

---

## 15. Environment Management

Every serious app has multiple environments.

```text
Local
Development
Staging
Production
```

Each environment has different:

- Database URL
- API URL
- Email keys
- Payment keys
- Google credentials
- WhatsApp credentials
- Storage bucket

Never hardcode secrets in code.

Use:

- `.env`
- Environment variables
- Secret manager
- Config files

---

## 16. Git and CI/CD

Manual deployment is fine in the beginning, but later you need automation.

Learn:

- Git
- Branches
- Pull requests
- GitHub Actions
- CI/CD pipeline
- Build step
- Test step
- Deploy step
- Rollback

Simple CI/CD flow:

```text
Developer pushes code
 ↓
GitHub Actions runs tests
 ↓
Build is created
 ↓
Code deployed to server
 ↓
PM2 restarts app
```

---

## 17. Docker

Docker helps package your application.

Learn:

- Image
- Container
- Dockerfile
- Docker Compose
- Volumes
- Networks
- Environment variables

Example container setup:

```text
Angular container
Node.js container
MongoDB container
Redis container
Nginx container
```

Docker helps make deployments more consistent.

---

## 18. Cloud Infrastructure

For AWS, start with:

| AWS Service | Purpose |
|---|---|
| EC2 | Virtual server |
| S3 | File storage |
| RDS | Managed SQL database |
| MongoDB Atlas / DocumentDB | MongoDB hosting |
| CloudFront | CDN |
| Route 53 | DNS |
| IAM | Permissions |
| VPC | Private network |
| Security Groups | Firewall rules |
| CloudWatch | Logs and monitoring |
| Lambda | Serverless functions |

For this type of application, common architecture:

```text
CloudFront
 ↓
Nginx / Load Balancer
 ↓
Angular frontend
 ↓
Node.js backend
 ↓
MongoDB Atlas
 ↓
S3 for files
 ↓
Redis for cache/queue
 ↓
Email/WhatsApp/Payment providers
```

---

## 19. Security

Security must be learned throughout, not only at the end.

Important topics:

- HTTPS everywhere
- Password hashing
- JWT expiry
- Refresh token rotation
- Input validation
- Rate limiting
- CORS
- Helmet
- SQL/NoSQL injection prevention
- File upload validation
- Role-based access
- API authorization
- Secrets management
- Server firewall
- Database access restriction
- Audit logs

Basic rule:

```text
Never trust frontend data.
Always validate again in the backend.
```

---

## 20. Performance

Performance means making the app fast and stable.

Frontend performance:

- Lazy loading
- Code splitting
- Image compression
- Caching
- CDN
- Minification
- Bundle size reduction

Backend performance:

- Database indexes
- Pagination
- Caching
- Avoid heavy synchronous work
- Queue background jobs
- Optimize API responses

Database performance:

- Indexes
- Aggregation optimization
- Query analysis
- Avoid unbounded queries
- Pagination
- Archiving old data

---

## 21. Caching

Caching reduces load.

Learn:

- Browser cache
- CDN cache
- Redis cache
- API response cache
- Database query cache

Example:

```text
Class categories do not change often
 ↓
Store in Redis
 ↓
Serve quickly without hitting database every time
```

---

## 22. Background Jobs and Queues

Not every task should happen during the user request.

Example:

```text
User enrolls in class
 ↓
API responds quickly
 ↓
Background job sends email, WhatsApp, push notification
```

Learn:

- Queue
- Worker
- Retry
- Failed jobs
- Delayed jobs
- Cron jobs
- BullMQ
- Redis

Use cases:

- Send emails
- Generate reports
- Send reminders
- Process payment proof
- Sync calendar events
- Expire payment links

---

## 23. Monitoring and Logging

You must know what is happening in production.

Learn:

- Application logs
- Error logs
- Access logs
- PM2 logs
- Nginx logs
- Database logs
- Uptime monitoring
- Alerting
- Performance monitoring

Questions to answer:

- Is the server up?
- Is the API slow?
- Which API is failing?
- Which user got an error?
- Why did payment fail?
- Was WhatsApp sent?
- Did Google Calendar event get created?

Tools:

- CloudWatch
- Sentry
- Grafana
- Prometheus
- UptimeRobot
- PM2 logs
- Nginx logs
- MongoDB Atlas monitoring

---

## 24. Backup and Disaster Recovery

This is production-grade knowledge.

Learn:

- Database backup
- File backup
- Point-in-time recovery
- Restore testing
- Server snapshot
- Multi-region backup
- Disaster recovery plan

Important rule:

```text
Backup is useless unless restore is tested.
```

You should know:

- How often is the database backed up?
- Where is the backup stored?
- Who can access the backup?
- How quickly can the app be restored?
- What happens if the server crashes?

---

## 25. Scaling

Scaling means handling more users.

Vertical scaling:

```text
Bigger server
More RAM
More CPU
```

Horizontal scaling:

```text
Multiple backend servers
Load balancer distributes traffic
```

Typical scaling path:

```text
Single server
 ↓
Separate database
 ↓
Add Redis
 ↓
Move files to S3
 ↓
Add load balancer
 ↓
Multiple backend servers
 ↓
CDN
 ↓
Queue workers
 ↓
Microservices only when needed
```

Do not start with microservices too early.

---

## 26. High Availability

High availability means the app should not go down easily.

Learn:

- Load balancer
- Multiple servers
- Managed database
- Auto restart
- Health checks
- Failover
- Zero-downtime deployment
- Blue-green deployment
- Rolling deployment

---

## 27. Cost Management

Important for cloud infrastructure.

Learn:

- Instance cost
- Storage cost
- Bandwidth cost
- Database cost
- Backup cost
- Logging cost
- API provider cost
- Cloud bill alerts
- Budgets
- Auto-scaling limits

For AWS, always set:

- Billing alerts
- Budget alerts
- IAM restrictions
- Security groups
- CloudWatch alarms

---

## 28. Production Architecture

Final production-level architecture:

```text
Users
 ↓
Domain / DNS
 ↓
Cloudflare / CDN
 ↓
Load Balancer / Nginx
 ↓
Frontend Angular App
 ↓
Backend Node.js APIs
 ↓
MongoDB Atlas
 ↓
Redis Cache / Queue
 ↓
S3 File Storage
 ↓
Email / WhatsApp / Payment / Google Calendar APIs
 ↓
Monitoring / Logging / Backup
```

---

# Best Learning Order

Follow this exact sequence:

1. What is a web application?
2. Frontend, backend, database
3. HTTP and APIs
4. Authentication and authorization
5. Database design
6. File uploads and storage
7. Notifications and integrations
8. Linux server basics
9. Deploy backend with PM2
10. Deploy frontend with Nginx
11. Domain, DNS, SSL
12. Environment variables
13. Git and deployment flow
14. Docker basics
15. Cloud basics
16. Security
17. Performance
18. Caching
19. Queues and background jobs
20. Monitoring and logging
21. Backup and disaster recovery
22. Scaling
23. High availability
24. Cost control
25. Full production architecture

---

# Final Mental Model

Whenever you think about infrastructure, think in this order:

```text
How does the user reach the app?
How does the frontend load?
How does the frontend call the backend?
How does the backend process business logic?
Where is data stored?
Where are files stored?
How are notifications sent?
How is the app secured?
How is it deployed?
How is it monitored?
How is it backed up?
How will it scale?
What happens when something fails?
```

---

# Suggested Practical Learning Path

## Phase 1: Local Understanding

Build and run a simple app locally:

```text
Angular frontend
Node.js backend
MongoDB database
```

Goal:

```text
Understand how frontend, backend, and database communicate.
```

## Phase 2: First Server Deployment

Deploy the backend and frontend on a Linux server.

Learn:

```text
SSH
PM2
Nginx
Domain
SSL
Logs
```

Goal:

```text
Make the app accessible through a real domain.
```

## Phase 3: Production Readiness

Add production features:

```text
Environment variables
File storage
Email/WhatsApp notifications
Error handling
Security middleware
Backups
Monitoring
```

Goal:

```text
Make the app safe, reliable, and maintainable.
```

## Phase 4: Scaling

Add:

```text
Redis
Queues
CDN
S3
Load balancer
Multiple backend instances
```

Goal:

```text
Make the app ready for more users and traffic.
```

## Phase 5: Mature Infrastructure

Add:

```text
CI/CD
Docker
Infrastructure as code
Observability
Disaster recovery
Cost controls
```

Goal:

```text
Operate the application like a professional production system.
```
