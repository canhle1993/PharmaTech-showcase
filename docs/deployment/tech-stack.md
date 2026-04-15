# Deployment and Tech Stack Notes

## Core Stack

### Frontend

- Angular
- TypeScript
- PrimeNG UI components
- Chart.js / Highcharts
- Socket.IO client

### Backend

- NestJS
- TypeScript
- MongoDB
- Mongoose
- JWT authentication
- Stripe integration
- Mailer integration
- Socket.IO
- OCR and AI modules

## Deployment Approach

The project is deployed to a cloud server and separated into:

- frontend static build served through Nginx
- backend NestJS API process managed with PM2
- MongoDB database connection via configured environment variables

## Delivery Workflow

- Source code maintained in a private GitHub repository
- Public-facing project explanation stored in a separate showcase repository
- Deployment automation handled with GitHub Actions
- Server publishing handled through SSH-based deployment steps

## Why This Matters For Recruiters

This project demonstrates not only feature development but also practical software delivery:

- environment configuration
- build and deploy workflow
- hosting setup
- API/frontend integration
- handling production/demo data

