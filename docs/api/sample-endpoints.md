# Sample API Endpoints

The backend is organized around a modular NestJS REST API. Below are representative endpoints that help explain the system scope without exposing the complete private codebase.

## Authentication

- `POST /api/auth/login`
- `POST /api/account/create`
- `POST /api/account/forgotPassword`
- `POST /api/account/verifyOtp`
- `POST /api/account/resetPassword`

## Products and Categories

- `GET /api/product/find-all`
- `GET /api/product/find-by-id/:id`
- `GET /api/product/:id/related`
- `POST /api/product/create`
- `PUT /api/product/update`
- `GET /api/product/export`
- `GET /api/category/find-all`
- `POST /api/category/create`
- `PUT /api/category/update`

## Cart, Wishlist, Orders

- `GET /api/cart/find-by-user/:userId`
- `POST /api/cart/add`
- `PUT /api/cart/update-quantity/:id`
- `GET /api/wishlist/find-by-user/:userId`
- `POST /api/wishlist/add`
- `POST /api/order/create`
- `POST /api/order/checkout`
- `POST /api/order/upload-proof/:id`
- `PUT /api/order/update-approval/:id`
- `PUT /api/order/mark-completed/:id`

## Quote and Contact

- `POST /api/mail/contact`
- `GET /api/quote/unread-count`
- `POST /api/quote/:id/reply`
- `GET /api/hotline`

## Career and Recruitment

- `POST /api/application/create`
- `GET /api/application/find-all`
- `GET /api/application/find-by-career/:career_id`
- `GET /api/career-analytics/overview`
- `GET /api/career-analytics/top-skills`
- `GET /api/career-analytics/funnel`

## AI, OCR, Analytics

- `POST /api/ai/chat`
- `POST /api/ocr/read`
- `GET /api/analytics/overview`
- `GET /api/analytics/products/by-category`
- `GET /api/order/chart/top-products`

These endpoints are included for showcase and explanation purposes only.

