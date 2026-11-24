# Binkeyit: full-stack MERN grocery delivery app

A quick-commerce shopping app in the style of a 10-minute grocery delivery service, built with MongoDB, Express, React and Node.js. Customers browse by category, search, fill a cart and pay online; admins manage the catalogue.

![Demo](Demo%201.gif)

## Features

**Customers**
- Sign up, log in, OTP email verification and password reset
- Browse categories and subcategories, search with infinite scroll, product detail pages
- Cart (including a mobile cart view), saved addresses and checkout
- Online payment with Stripe, or cash on delivery
- Order history and profile management

**Admins**
- Manage categories, subcategories and products
- Upload product images (stored on Cloudinary)

## Tech stack

| Part | Tools |
|---|---|
| Client | React 18, Vite, Redux Toolkit, React Router, Tailwind CSS, Axios, React Hook Form, Stripe.js |
| Server | Node.js, Express, MongoDB with Mongoose, JWT (access and refresh tokens), bcrypt, Multer |
| Services | Cloudinary (images), Resend (email), Stripe (payments and webhooks) |

## Getting started

You need Node.js and a MongoDB database, plus Cloudinary, Resend and Stripe accounts.

### Server

```bash
cd server
npm install
npm run dev
```

Create `server/.env`:

```
FRONTEND_URL=http://localhost:5173
MONGODB_URI=
SECRET_KEY_ACCESS_TOKEN=
SECRET_KEY_REFRESH_TOKEN=
RESEND_API=
CLODINARY_CLOUD_NAME=
CLODINARY_API_KEY=
CLODINARY_API_SECRET_KEY=
STRIPE_SECRET_KEY=
STRIPE_ENPOINT_WEBHOOK_SECRET_KEY=
```

The variable names are spelled exactly as the code reads them, including `CLODINARY` and `ENPOINT`.

The server listens on port `8080`. (`server/index.js` sets `PORT = 8080 || process.env.PORT`, so a `PORT` variable is currently ignored.)

### Client

```bash
cd client
npm install
npm run dev
```

Create `client/.env`:

```
VITE_API_URL=http://localhost:8080
VITE_STRIPE_PUBLIC_KEY=
```

## API overview

| Route | Purpose |
|---|---|
| `/api/user` | Registration, login, verification, password reset, profile |
| `/api/category`, `/api/subcategory` | Catalogue structure |
| `/api/product` | Products, search, listing |
| `/api/cart` | Cart items |
| `/api/address` | Delivery addresses |
| `/api/order` | Checkout, Stripe payment and webhook, order history |
| `/api/file` | Image upload |

## Deployment

The server includes a `vercel.json` for deploying to Vercel. Deploy the client as a static Vite build and point `VITE_API_URL` at the server.

## License

[MIT](LICENSE)
