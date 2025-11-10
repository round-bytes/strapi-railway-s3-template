# 🚀 Strapi v5 Template for Railway with S3 Uploads (Local in Dev)

This is a **Strapi v5** template optimized for **Railway** with **S3 uploads in production** and **local uploads in development**. Strapi provides a headless CMS with a powerful admin panel and REST/GraphQL APIs.

> **Note:** In development, uploads are stored locally in `public/uploads`. In production (e.g., on Railway), uploads are stored on S3 using the official provider.

You can **clone or fork** this repo to create your own Strapi project with the same baseline configuration.

## ✨ Features

- **Strapi v5** - Latest version with all the newest features
- **S3 Uploads (Production)** - Files stored on your S3 bucket via `aws-s3` provider
- **Local Uploads (Development)** - Files stored locally in `public/uploads`
- **Railway Ready** - Pre-configured for seamless Railway deployment
- **Highly Customizable** - Separate development and production environment configurations
- **TypeScript** - Full TypeScript support for better development experience

## 🚀 Getting Started

```bash
npm install
npm run build
npm run develop
```

> **Note:** This template uses `npm` by default. If you want to use `yarn`, update the commands in `railway.toml` to replace `npm` with `yarn` so Railway runs the correct scripts.

## 🎯 Customization

This template is highly customizable thanks to its **separate development and production environment configurations**. You can find environment-specific settings in:

- `config/env/development/` - Development environment settings
  - `database.ts` - Database configuration for local development
  - `plugins.ts` - Plugin configurations (local upload by default)
  - `server.ts` - Server settings

- `config/env/production/` - Production environment settings
  - `database.ts` - Production database configuration (PostgreSQL)
  - `plugins.ts` - Production plugin settings (S3 upload provider)
  - `server.ts` - Production server configuration

This separation allows you to easily customize settings for each environment without affecting the other.

## 🔧 Environment Variables

The template expects the following environment variables (set locally via `.env`, and on Railway via project variables):

### Development (.env)
- Strapi security keys (JWT secrets, API tokens, encryption keys)
- Database configuration (SQLite or your choice)
- Server settings (host, port)
- No S3 variables are required in development (uploads are local)

### Production (Railway variables)
- All required Strapi security keys
- PostgreSQL database configuration with Railway integration
- Production server settings
- `STRAPI_URL` - Public URL of your Strapi app (e.g., `https://your-app.up.railway.app` or your custom domain)
- S3 upload provider variables:
  - `AWS_ACCESS_KEY_ID` - IAM access key ID
  - `AWS_ACCESS_SECRET` - IAM secret access key
  - `AWS_BUCKET` - S3 bucket name
  - `AWS_ACL` - Object ACL, defaults to `public-read` (optional)
  - `AWS_CDN_URL` - Optional base URL for files (use your CDN or S3 website URL). If not set, the provider falls back to the default S3 URL.

**Important:** Before deploying, make sure to:
1. Create a `.env` file for local development
2. Set environment variables on Railway for production
3. Generate secure values for all security keys (never use the default "tobemodified" values)
4. Create and configure an S3 bucket and IAM user with permissions to `PutObject`, `GetObject`, and `DeleteObject` in your bucket

#### Example (Production variables on Railway)

```bash
# Public URL
STRAPI_URL=https://your-app.up.railway.app

# AWS S3 (uploads in production)
AWS_ACCESS_KEY_ID=YOUR_AWS_ACCESS_KEY_ID
AWS_ACCESS_SECRET=YOUR_AWS_SECRET_ACCESS_KEY
AWS_BUCKET=your-bucket-name
# Optional
AWS_ACL=public-read
AWS_CDN_URL=https://cdn.example.com
```

## 🚂 Strapi with Railway

This template is optimized for Railway deployment:

- **Railway Configuration** - Includes `railway.toml` with build and deployment settings
- **Uploads Storage**
  - Development: local storage in `public/uploads` (no S3 required)
  - Production: S3 bucket via `aws-s3` provider (no Railway volumes needed)
- **PostgreSQL Integration** - Production environment automatically uses Railway's PostgreSQL service
- **Environment Variables** - Production env file includes Railway-specific variable references
- **Auto Redeploys** - Once connected to Railway, any push to your repo triggers a fresh Railway deploy

The `railway.toml` file configures:
- Build process using Nixpacks
- Node.js 22 runtime
- Build and start commands

Strapi comes with a full featured [Command Line Interface](https://docs.strapi.io/dev-docs/cli) (CLI) which lets you scaffold and manage your project in seconds.

### `develop`

Start your Strapi application with autoReload enabled. [Learn more](https://docs.strapi.io/dev-docs/cli#strapi-develop)

```
npm run develop
# or
yarn develop
```

### `start`

Start your Strapi application with autoReload disabled. [Learn more](https://docs.strapi.io/dev-docs/cli#strapi-start)

```
npm run start
# or
yarn start
```

### `build`

Build your admin panel. [Learn more](https://docs.strapi.io/dev-docs/cli#strapi-build)

```
npm run build
# or
yarn build
```

## ⚙️ Deployment

Strapi gives you many possible deployment options for your project including [Strapi Cloud](https://cloud.strapi.io). Browse the [deployment section of the documentation](https://docs.strapi.io/dev-docs/deployment) to find the best solution for your use case.

```
yarn strapi deploy
```

## 📚 Learn more

- [Resource center](https://strapi.io/resource-center) - Strapi resource center.
- [Strapi documentation](https://docs.strapi.io) - Official Strapi documentation.
- [Strapi tutorials](https://strapi.io/tutorials) - List of tutorials made by the core team and the community.
- [Strapi blog](https://strapi.io/blog) - Official Strapi blog containing articles made by the Strapi team and the community.
- [Changelog](https://strapi.io/changelog) - Find out about the Strapi product updates, new features and general improvements.

Feel free to check out the [Strapi GitHub repository](https://github.com/strapi/strapi). Your feedback and contributions are welcome!

## ✨ Community

- [Discord](https://discord.strapi.io) - Come chat with the Strapi community including the core team.
- [Forum](https://forum.strapi.io/) - Place to discuss, ask questions and find answers, show your Strapi project and get feedback or just talk with other Community members.
- [Awesome Strapi](https://github.com/strapi/awesome-strapi) - A curated list of awesome things related to Strapi.

---

<sub>🤫 Psst! [Strapi is hiring](https://strapi.io/careers).</sub>