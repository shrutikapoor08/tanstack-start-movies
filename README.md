# TanStack Netflix Example

A Netflix-style movie browsing application built with TanStack Router, React 19, and Tailwind CSS v4. This app demonstrates modern React patterns, file-based routing, and integration with The Movie Database (TMDB) API.

## Features

- 🎬 Browse popular movies from TMDB API
- 🎨 Netflix-inspired dark theme design
- 📱 Responsive layout with Tailwind CSS v4
- 🛣️ File-based routing with TanStack Router
- ⚡ Fast development with Vite
- 🔍 Movie search and filtering capabilities
- 💾 TypeScript for type safety
- 🧪 Testing setup with Vitest

## Project Structure

```
src/
├── components/          # Reusable UI components
│   └── Header.tsx      # Navigation header component
├── routes/             # File-based routing
│   ├── __root.tsx     # Root layout with header and devtools
│   ├── index.tsx      # Home page with React logo
│   └── fetch-movies.tsx # Movies catalog page
├── types/              # TypeScript type definitions
│   └── movie.ts       # Movie and TMDB API types
├── router.tsx         # Router configuration
├── styles.css         # Global styles with Tailwind
└── routeTree.gen.ts   # Auto-generated route tree
```

## Getting Started

### Prerequisites

- Node.js 18+ 
- npm or yarn
- TMDB API key (for movie data)

### Installation

1. Clone the repository:
```bash
git clone <repository-url>
cd tanstack-example-netflix
```

2. Install dependencies:
```bash
npm install
```

3. Set up environment variables:
```bash
# Create .env file and add your TMDB API token
TMDB_AUTH_TOKEN=your_tmdb_bearer_token_here
```

4. Start the development server:
```bash
npm run dev
```

The app will be available at `http://localhost:3000`.

## Available Scripts

- `npm run dev` - Start development server on port 3000
- `npm run build` - Build for production
- `npm run serve` - Preview production build
- `npm run test` - Run tests with Vitest
- `npm run lint` - Run ESLint
- `npm run format` - Format code with Prettier
- `npm run check` - Run both linting and formatting

## Routes

- `/` - Home page with React logo and getting started links
- `/fetch-movies` - Movies catalog displaying popular movies from TMDB

## API Integration

The app integrates with The Movie Database (TMDB) API to fetch movie data:

- **Endpoint**: `https://api.themoviedb.org/3/discover/movie`
- **Authentication**: Bearer token required
- **Data**: Popular movies with posters, ratings, and descriptions

### Movie Data Structure

```typescript
interface Movie {
  id: number
  title: string
  overview: string
  poster_path: string | null
  backdrop_path: string | null
  release_date: string
  vote_average: number
  popularity: number
}
```

## Styling

This project uses **Tailwind CSS v4** for styling with a Netflix-inspired dark theme:

- Dark background with gradient effects
- Glass morphism effects with backdrop blur
- Hover animations and transitions
- Responsive grid layouts
- Custom color palette matching Netflix branding

### Key Design Elements

- **Colors**: Black backgrounds with red accents (#e50914)
- **Typography**: Clean, modern fonts with proper hierarchy
- **Cards**: Glass effect with hover scale animations
- **Layout**: Responsive grid system for movie cards

## Components

### Header Component
- Navigation links between routes
- Clean white background with black text
- Responsive design

### Movie Card Component
- Displays movie poster, title, overview, and rating
- Hover effects with scale animation
- Glass morphism styling
- Accessible with proper ARIA labels

## Development

### Adding New Routes

Create a new file in `src/routes/` directory. TanStack Router will automatically generate the route configuration.

Example:
```tsx
// src/routes/about.tsx
import { createFileRoute } from '@tanstack/react-router'

export const Route = createFileRoute('/about')({
  component: About,
})

function About() {
  return <div>About page content</div>
}
```

### Data Loading

Routes can load data using the `loader` function:

```tsx
export const Route = createFileRoute('/movies')({
  component: MoviesPage,
  loader: async () => {
    const response = await fetch('/api/movies')
    return response.json()
  },
})
```

### TypeScript

The project is fully typed with TypeScript. Key type definitions are in:
- `src/types/movie.ts` - Movie and API response types
- Auto-generated router types for type-safe navigation

## Testing

Tests are written using Vitest and React Testing Library:

```bash
npm run test
```

## Linting & Formatting

The project uses ESLint and Prettier with TanStack's configuration:

```bash
npm run lint    # Check for linting errors
npm run format  # Format code
npm run check   # Run both linting and formatting
```

## Building for Production

```bash
npm run build
```

This creates an optimized production build in the `dist/` directory.

## Environment Variables

- `TMDB_AUTH_TOKEN` - Bearer token for TMDB API authentication

## Technologies Used

- **React 19** - Latest React with concurrent features
- **TanStack Router** - Type-safe file-based routing
- **TypeScript** - Static type checking
- **Tailwind CSS v4** - Utility-first CSS framework
- **Vite** - Fast build tool and dev server
- **Vitest** - Fast unit testing framework
- **ESLint & Prettier** - Code quality and formatting

## Learn More

- [TanStack Router Documentation](https://tanstack.com/router)
- [React 19 Documentation](https://react.dev)
- [Tailwind CSS v4 Documentation](https://tailwindcss.com)
- [TMDB API Documentation](https://developers.themoviedb.org/3)
- [Vite Documentation](https://vitejs.dev)

## License

This project is for educational purposes and demonstrates modern React development patterns with TanStack tools.