# ✈️ Flights Booking Service

A robust backend service for flight bookings, built with Node.js, Express, and Sequelize.

---

## 🚀 Key Features

### 🛡️ Advanced & Production-Ready

- **Idempotent Payment API**  
  Prevents double-charging with idempotency keys for safe, repeatable payment requests.

- **Automated Booking Cleanup**  
  Uses scheduled cron jobs to auto-cancel unpaid bookings, keeping inventory accurate and available.

- **Transactional Integrity**  
  All critical operations (booking, payment, cancellation) are fully transaction-safe, ensuring data consistency.

- **Comprehensive Logging**  
  Integrated with Winston for timestamped, multi-transport logs (console & file), supporting real-world monitoring and debugging.

- **API Versioning**  
  All endpoints are namespaced under `/api/v1` for seamless future upgrades.

---

### 🧩 Core Functionality

- **Create Bookings**  
  Reserve seats on flights, with real-time seat availability and cost calculation.

- **Secure Payments**  
  Validates user, amount, and booking status before confirming payment.

- **Automatic Status Management**  
  Bookings transition through `initiated`, `pending`, `booked`, and `cancelled` states, managed via enums.

- **Health Check Endpoint**  
  `/api/v1/info` for quick API status verification.

---

## 🛠️ Tech Stack

- **Node.js** + **Express**
- **Sequelize** (ORM & migrations)
- **Winston** (logging)
- **node-cron** (scheduled jobs)
- **dotenv** (config management)

---

## ⚡ Quick Start

```bash
git clone <repo-url>
cd Flights-Booking
npm install
# Set up your .env file (see src/config/server-config.js for required vars)
npx sequelize-cli db:migrate
npm start
```

---

## 📚 API Endpoints

- `POST /api/v1/bookings` – Create a booking
- `POST /api/v1/bookings/payments` – Make a payment (requires `x-idempotency-key`)
- `GET /api/v1/info` – Health check

---

## 📝 Notes

- All operations are transaction-safe and error-handled with custom error classes.
- Cron jobs run every 30 minutes to clean up stale bookings.
- Logging is production-ready out of the box.

---

**Built for reliability, extensibility, and real-world scale.**