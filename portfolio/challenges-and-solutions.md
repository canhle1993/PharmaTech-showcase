# Challenges and Solutions

## 1. Broad Project Scope

### Challenge

The project was not a narrow single-purpose website. It combined:

- product showcase
- quotation workflow
- ordering and payment
- recruitment
- support and content management

This made consistency across modules more difficult.

### Solution

We separated the system into clear functional areas on both frontend and backend, then worked module by module to keep the implementation understandable and maintainable.

## 2. Demo Deployment On A Real Server

### Challenge

Getting both frontend and backend running reliably online required server setup, environment handling, PM2/Nginx coordination, and database connectivity.

### Solution

We deployed the frontend and backend separately, configured server processes, and automated publishing using GitHub Actions so changes could be delivered more smoothly.

## 3. Handling Media, Uploads, and Demo Data

### Challenge

The project includes product images, banners, resumes, payment proof, and other uploaded files. Demo environments can easily break if these assets are missing or paths are inconsistent.

### Solution

We standardized upload paths, aligned frontend image URLs with backend configuration, and restored demo data and media carefully to keep the live version usable for presentation.

## 4. Making A Public Showcase Without Exposing Source Code

### Challenge

The real project repository is private, but recruiters still need something clear and professional to review.

### Solution

I created a separate showcase approach with:

- recruiter-friendly README
- screenshots
- flow diagrams
- portfolio notes
- live demo references

This preserves source privacy while still presenting the project professionally.

