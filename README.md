# Hello World React App 🐉

A simple Hello World React app with a dragon and some cool effects, all containerized with Docker.

## What You Need

Before you can run this thing, make sure you have:

- **Node.js** (v18 or higher) - grab it from [nodejs.org](https://nodejs.org/)
- **npm** - comes with Node.js, so you're good
- **Docker** - get Docker Desktop from [docker.com](https://www.docker.com/products/docker-desktop)

Check if you have everything:
```bash
node --version
npm --version
docker --version
```

## Dependencies

The app uses these main packages (check `package.json` for exact versions):

- `react` & `react-dom` - the React framework
- `react-scripts` - build tools and config
- Testing libraries (`@testing-library/react`, etc.) - for running tests
- `web-vitals` - performance metrics

## Installation

1. Clone the repo:
```bash
git clone <your-repo-url>
cd classIntro
```

2. Install all the npm packages:
```bash
npm install
```

That's it! Should take a minute or two.

## Running the App

### Local Development

Just run:
```bash
npm start
```

This fires up the dev server and opens your browser to `http://localhost:3000`. You'll see the dragon and all the cool effects.

### Production Build

To build it for production:
```bash
npm run build
```

This creates an optimized build in the `build` folder.

## Running with Docker

### Build the Image

First, build the Docker image:
```bash
docker build -t hello-world-app .
```

This might take a bit the first time since it's downloading base images and installing dependencies.

### Run the Container

Once it's built, run it:
```bash
docker run -d -p 8080:80 --name hello-world-container hello-world-app
```

The app will be running at `http://localhost:8080`

### Managing the Container

- Stop it: `docker stop hello-world-container`
- Start it again: `docker start hello-world-container`
- Remove it: `docker rm -f hello-world-container`
- Check if it's running: `docker ps`

## Project Structure

```
classIntro/
├── public/          # Static files
├── src/            # Source code
│   ├── App.js      # Main component (has the dragon 🐉)
│   ├── App.css     # Styles with all the cool effects
│   └── index.js    # Entry point
├── Dockerfile      # Docker config
├── package.json    # Dependencies and scripts
└── README.md       # This file
```

## Available Scripts

- `npm start` - Run in dev mode (hot reload enabled)
- `npm run build` - Build for production
- `npm test` - Run tests
- `npm run eject` - Eject from Create React App (one-way, don't do this unless you know what you're doing)

## Docker Details

The Dockerfile uses a multi-stage build:
1. **Build stage** - Uses Node.js to install deps and build the React app
2. **Production stage** - Uses nginx to serve the built files

This keeps the final image small since we don't need all the build tools in production.

## Notes

- The app has a dragon with fire effects, animated stars, and glowing text
- All the styling is in `App.css` if you want to mess with it
- The Docker container runs nginx on port 80, mapped to 8080 on your host
