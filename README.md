# Nestly

A full-stack rental listing platform where property owners can list rentals and guests can book short-term stays or long-term rentals.

## Features

- **Property Listings** — Owners can create, edit, and delete listings with multiple image uploads
- **Dual Booking Types** — Supports both short-term (check-in/check-out) and long-term (monthly) rental bookings
- **Booking Management** — Owners can accept or reject booking requests; guests can cancel bookings
- **Role-Based Dashboards** — Separate dashboards for guests and property owners
- **Reviews & Ratings** — Authenticated users can leave star ratings and comments on listings
- **Search** — Filter listings by location with case-insensitive partial matching
- **Authentication** — Secure signup/login with Passport.js local strategy
- **Image Uploads** — Cloudinary-backed multi-image upload and deletion per listing
- **Flash Notifications** — Success and error feedback across all user actions

---

## Tech Stack

| Layer | Technology |
|---|---|
| Runtime | Node.js |
| Framework | Express.js |
| Templating | EJS + ejs-mate |
| Database | MongoDB + Mongoose |
| Authentication | Passport.js (passport-local-mongoose) |
| Image Storage | Cloudinary + Multer |
| Session Store | connect-mongo |
| Validation | Joi |

---

## Project Structure

```
nestly/
├── controllers/        # Route handler logic
│   ├── bookingController.js
│   ├── listing.js
│   ├── review.js
│   └── user.js
├── models/             # Mongoose schemas
│   ├── booking.js
│   ├── listing.js
│   ├── review.js
│   └── user.js
├── routes/             # Express routers
│   ├── bookingRoutes.js
│   ├── home.js
│   ├── listing.js
│   ├── review.js
│   └── user.js
├── views/              # EJS templates
├── public/             # Static assets (CSS, JS)
├── utils/              # ExpressError, wrapAsync helpers
├── middleware.js        # Auth, validation, role middleware
├── schema.js           # Joi validation schemas
├── cloudConfig.js      # Cloudinary configuration
├── app.js              # App entry point
└── vercel.json         # Vercel deployment config
```

---

## Getting Started

### Prerequisites

- [Node.js](https://nodejs.org/) v18+
- [MongoDB Atlas](https://www.mongodb.com/atlas) account (or local MongoDB)
- [Cloudinary](https://cloudinary.com/) account

### Installation

```bash
git clone https://github.com/Rishaubkumar/nestly.git
cd nestly
npm install
```

### Environment Variables

Create a `.env` file in the root directory:

```env
ATLASDB_URL=your_mongodb_atlas_connection_string
SECRET=your_session_secret_key
CLOUD_NAME=your_cloudinary_cloud_name
CLOUD_API_KEY=your_cloudinary_api_key
CLOUD_API_SECRET=your_cloudinary_api_secret
```

### Run Locally

```bash
# Development (with auto-restart)
npm run dev

# Production
npm start
```

Server runs at `http://localhost:8080`

---

## API Routes

| Method | Route | Description |
|---|---|---|
| GET | `/home` | Landing page |
| GET | `/listings` | Browse all listings |
| GET | `/listings/:id` | View a listing |
| POST | `/listings` | Create a listing (owner) |
| PUT | `/listings/:id` | Update a listing (owner) |
| DELETE | `/listings/:id` | Delete a listing (owner) |
| POST | `/listings/:id/reviews` | Add a review |
| DELETE | `/listings/:id/reviews/:reviewId` | Delete a review |
| POST | `/bookings` | Create a booking |
| POST | `/bookings/:id/cancel` | Cancel a booking |
| GET | `/owner/dashboard` | Owner booking dashboard |
| GET | `/user/dashboard` | Guest booking dashboard |
| POST | `/owner/accept` | Accept a booking |
| GET | `/signup` | Register |
| POST | `/login` | Login |
| GET | `/logout` | Logout |

---

## Contributing

1. Fork the repository
2. Create a feature branch: `git checkout -b feature/your-feature`
3. Commit your changes: `git commit -m 'feat: add your feature'`
4. Push to the branch: `git push origin feature/your-feature`
5. Open a Pull Request

---

## License

This project is open source and available under the [MIT License](LICENSE).
