# Plantation Management

An early-stage scaffold for a plantation management platform with a React client and a microservice-style Node.js API gateway.

![React](https://img.shields.io/badge/React-20232A?style=for-the-badge&logo=react&logoColor=61DAFB)
![Vite](https://img.shields.io/badge/Vite-646CFF?style=for-the-badge&logo=vite&logoColor=white)
![Redux](https://img.shields.io/badge/Redux-764ABC?style=for-the-badge&logo=redux&logoColor=white)
![Node.js](https://img.shields.io/badge/Node.js-339933?style=for-the-badge&logo=nodedotjs&logoColor=white)
![Express](https://img.shields.io/badge/Express-000000?style=for-the-badge&logo=express&logoColor=white)
![MongoDB](https://img.shields.io/badge/MongoDB-47A248?style=for-the-badge&logo=mongodb&logoColor=white)

## About

This repo lays the groundwork for a plantation management system built as separate services behind a single API gateway. The gateway, the client shell and a shared models package are in place; the individual services (auth, users, donations, tasks, inventory) have not been added yet. It is a work in progress.

## What's Here

- **API gateway** (`apiGateway/app.js`): an Express server on port `5000` that proxies requests with `http-proxy-middleware`:

  | Path prefix | Forwards to |
  | --- | --- |
  | `/auth` | `http://localhost:5001` |
  | `/users` | `http://localhost:5002` |
  | `/donations` | `http://localhost:5003` |
  | `/tasks` | `http://localhost:5004` |
  | `/inventory` | `http://localhost:5005` |

- **MongoDB helper** (`apiGateway/config/db.js`): connects with Mongoose using `MONGODB_URI`
- **Shared models package** (`models/`, published name `@shared/models`): a placeholder for Mongoose schemas shared across services
- **Client** (`client/`): React 18 + Vite app with React Router (placeholder `/`, `/login` and `/signup` routes) and an empty Redux Toolkit store

## Tech Stack

| Part | Technology |
| --- | --- |
| Client | React 18, Vite, React Router, Redux Toolkit |
| Gateway | Node.js, Express, http-proxy-middleware |
| Database | MongoDB, Mongoose |

## Project Structure

```
plantation-management/
├── apiGateway/
│   ├── app.js           # reverse proxy to the services
│   └── config/db.js     # Mongoose connection
├── models/              # @shared/models package (schemas to come)
│   └── model/User.js
└── client/              # React + Vite front end
    └── src/
        ├── App.jsx      # routes
        └── redux/store.js
```

## Getting Started

### Prerequisites

- Node.js and npm
- MongoDB (for services that will use `connectDB`)

### Client

```bash
cd client
npm install
npm run dev       # start the Vite dev server
npm run build     # production build
npm run preview   # preview the build
npm run lint      # ESLint
```

### API gateway

```bash
cd apiGateway
npm install
node app.js
```

### Environment variables

| Variable | Used in |
| --- | --- |
| `MONGODB_URI` | `apiGateway/config/db.js` |

## Author

**Aryan Bhandari**: [GitHub](https://github.com/aryanbha123)
