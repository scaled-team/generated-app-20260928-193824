# ChatBoard Pro

A high-performance, real-time chat application template architected for the edge. This project demonstrates a sophisticated implementation of Cloudflare Workers, Durable Objects, and Hono, paired with a modern React frontend.

[cloudflarebutton]

## 🚀 Overview

ChatBoard Pro provides a robust foundation for building scalable, stateful applications on Cloudflare's global network. It leverages a unique "Entity-Index" pattern to manage persistent state across Durable Objects while maintaining efficient listing and search capabilities.

### Key Features

- **Edge-Resident State**: Utilizes Cloudflare Durable Objects for consistent, low-latency data storage for Users and Chat Boards.
- **Transactional Indexing**: Implements a custom indexing system within Durable Objects to allow for paginated listing of entities.
- **Type-Safe Architecture**: Shared TypeScript types ensure end-to-end consistency between the Worker API and the React frontend.
- **Modern UI/UX**: Built with React 18, Tailwind CSS, and a comprehensive suite of Shadcn/UI components.
- **Responsive Design**: Fully mobile-optimized layout with a configurable sidebar system.
- **Resilient Error Handling**: Integrated client-side error reporting and a robust backend error handling middleware.

## 🛠️ Tech Stack

- **Frontend**: [React](https://reactjs.org/), [Vite](https://vitejs.dev/), [Tailwind CSS](https://tailwindcss.com/), [Shadcn/UI](https://ui.shadcn.com/)
- **Backend**: [Cloudflare Workers](https://workers.cloudflare.com/), [Hono](https://hono.dev/)
- **Storage**: [Cloudflare Durable Objects](https://developers.cloudflare.com/workers/runtime-apis/durable-objects/)
- **Package Manager**: [Bun](https://bun.sh/)
- **Icons**: [Lucide React](https://lucide.dev/)

## 📂 Project Structure

```text
├── shared/            # Shared types and mock data
├── src/               # React frontend application
│   ├── components/    # UI components and layout
│   ├── hooks/         # Custom React hooks
│   ├── lib/           # Utilities and API client
│   └── pages/         # Application views
├── worker/            # Cloudflare Worker source
│   ├── core-utils.ts  # Durable Object entity framework
│   ├── entities.ts    # Business logic entities
│   └── user-routes.ts # API route definitions
└── wrangler.jsonc     # Cloudflare configuration
```

## 💻 Getting Started

### Prerequisites

- [Bun](https://bun.sh/) installed on your local machine.
- A [Cloudflare account](https://dash.cloudflare.com/sign-up) with Workers and Durable Objects enabled.

### Installation

1. Clone the repository:
   ```bash
   git clone <repository-url>
   cd <project-directory>
   ```

2. Install dependencies:
   ```bash
   bun install
   ```

### Local Development

1. Start the development server (runs both Vite and Wrangler):
   ```bash
   bun run dev
   ```

2. Open [http://localhost:5173](http://localhost:5173) in your browser.

## ☁️ Deployment

Deploying to Cloudflare is seamless. The project is configured to bundle the frontend and backend into a single Worker deployment.

### Automated Deployment

[cloudflarebutton]

### Manual Deployment

1. Login to your Cloudflare account:
   ```bash
   bunx wrangler login
   ```

2. Deploy the application:
   ```bash
   bun run deploy
   ```

Note: Ensure your `wrangler.jsonc` (or `wrangler.toml`) is correctly configured with your account ID and desired script name.

## 🧪 Usage

### Entity Pattern
The project uses a base `Entity` and `IndexedEntity` class in `worker/core-utils.ts`. To create a new data type:
1. Define the type in `shared/types.ts`.
2. Extend `IndexedEntity` in `worker/entities.ts`.
3. Register routes in `worker/user-routes.ts`.

### API Communication
Use the provided `api` client in `src/lib/api-client.ts` for type-safe requests:
```typescript
import { api } from "@/lib/api-client";
import { User } from "@shared/types";

const users = await api<User[]>("/api/users");
```

## 🛡️ License

This project is licensed under the MIT License - see the LICENSE file for details.

---
*Powered by DelegateBuild*