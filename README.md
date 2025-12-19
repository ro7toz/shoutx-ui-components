# ShoutX UI Component Library

🎨 **60+ Production-Ready React UI Components** for the ShoutX Instagram Shoutout Exchange Platform

## Features

✨ **60+ Components**: Complete UI kit with all essential components
✅ **Built with Radix UI**: Accessible, unstyled primitives
🎯 **Tailwind CSS**: Modern, responsive styling
💎 **TypeScript**: Full type safety
🌙 **Dark Mode**: Built-in theme support
🔄 **Contexts**: Pre-built Auth and Data contexts
📱 **Responsive**: Mobile-first design
♿ **Accessible**: WCAG compliant

## Components Included

### Inputs & Forms
- Accordion
- Button
- Card
- Checkbox
- Form (with react-hook-form)
- Input
- Input OTP
- Label
- Radio Group
- Select
- Switch
- Textarea
- Popover
- Calendar
- ComboBox

### Layout
- Alert
- Alert Dialog
- Badge
- Breadcrumb
- Dialog
- Drawer
- Navigation Menu
- Sidebar (Collapsible)
- Sheet
- Tabs
- Resizable Panels
- Scroll Area

### Data Display
- Table
- Carousel
- Progress
- Hover Card
- Pagination
- Slider
- Sonner (Toast)

### Dropdowns & Menus
- Dropdown Menu
- Context Menu
- Menubar

### Advanced
- Toggle
- Toggle Group
- Tooltip
- Skeleton
- Collapsible
- Command
- AspectRatio
- Avatar

### Hooks
- useIsMobile
- useSidebar
- useCarousel
- useFormField

## Installation

```bash
npm install shoutx-ui-components
# or
yarn add shoutx-ui-components
# or
pnpm add shoutx-ui-components
```

## Setup

### 1. Tailwind Configuration

```js
// tailwind.config.ts
import type { Config } from 'tailwindcss';

const config: Config = {
  content: [
    './src/components/**/*.{js,ts,jsx,tsx}',
    './src/pages/**/*.{js,ts,jsx,tsx}',
  ],
  theme: {
    extend: {
      colors: {
        primary: 'hsl(173, 58%, 39%)',
        secondary: 'hsl(0, 0%, 96%)',
      },
    },
  },
  plugins: [],
};

export default config;
```

### 2. Import Styles

```css
/* globals.css */
@tailwind base;
@tailwind components;
@tailwind utilities;
```

## Usage Examples

### Button

```tsx
import { Button } from '@/components/ui/button';

export function ButtonDemo() {
  return (
    <div className="flex gap-2">
      <Button>Default</Button>
      <Button variant="secondary">Secondary</Button>
      <Button variant="destructive">Destructive</Button>
      <Button variant="outline">Outline</Button>
      <Button variant="ghost">Ghost</Button>
      <Button variant="link">Link</Button>
    </div>
  );
}
```

### Card

```tsx
import { Card, CardContent, CardDescription, CardHeader, CardTitle } from '@/components/ui/card';

export function CardDemo() {
  return (
    <Card>
      <CardHeader>
        <CardTitle>Card Title</CardTitle>
        <CardDescription>Card description goes here</CardDescription>
      </CardHeader>
      <CardContent>
        <p>Card content</p>
      </CardContent>
    </Card>
  );
}
```

### Form with Validation

```tsx
import { useForm } from 'react-hook-form';
import { Form, FormControl, FormField, FormItem, FormLabel, FormMessage } from '@/components/ui/form';
import { Input } from '@/components/ui/input';
import { Button } from '@/components/ui/button';

export function FormDemo() {
  const form = useForm();

  return (
    <Form {...form}>
      <form onSubmit={form.handleSubmit(onSubmit)} className="space-y-8">
        <FormField
          control={form.control}
          name="username"
          render={({ field }) => (
            <FormItem>
              <FormLabel>Username</FormLabel>
              <FormControl>
                <Input placeholder="johndoe" {...field} />
              </FormControl>
              <FormMessage />
            </FormItem>
          )}
        />
        <Button type="submit">Submit</Button>
      </form>
    </Form>
  );
}
```

### Auth Context

```tsx
import { AuthProvider, useAuth } from '@/contexts/AuthContext';

function App() {
  return (
    <AuthProvider>
      <YourApp />
    </AuthProvider>
  );
}

function YourComponent() {
  const { user, login, logout } = useAuth();

  return (
    <div>
      {user ? (
        <>
          <p>Welcome, {user.name}!</p>
          <button onClick={logout}>Logout</button>
        </>
      ) : (
        <button onClick={() => login('email@example.com', 'password')}>Login</button>
      )}
    </div>
  );
}
```

## Project Structure

```
shoutx-ui-components/
├── components/ui/
│   ├── accordion.tsx
│   ├── alert.tsx
│   ├── badge.tsx
│   ├── button.tsx
│   ├── card.tsx
│   ├── [... 50+ more components ...]
│   └── utils.ts
├── contexts/
│   ├── AuthContext.tsx
│   └── DataContext.tsx
├── pages/
│   ├── DashboardPage.tsx
│   ├── ProfilePage.tsx
│   ├── TermsPage.tsx
│   └── [... more pages ...]
├── hooks/
│   └── use-mobile.ts
├── tailwind.config.ts
├── tsconfig.json
├── package.json
└── README.md
```

## Contexts Included

### AuthContext

Manages user authentication state with mock user data.

```tsx
interface User {
  id: string;
  name: string;
  username: string;
  email: string;
  profilePicture: string;
  planType: 'basic' | 'pro';
  followers: number;
  accountType: string;
  isVerified: boolean;
  rating: number;
  strikes: number;
  dailyRequestsSent: number;
  dailyRequestsAccepted: number;
  mediaItems: MediaItem[];
}
```

### DataContext

Manages shoutout requests, exchanges, and notifications.

```tsx
interface ShoutoutRequest {
  id: string;
  senderId: string;
  receiverId: string;
  status: 'pending' | 'accepted' | 'completed' | 'expired';
  createdAt: Date;
  completedAt?: Date;
}

interface Exchange {
  id: string;
  user1Id: string;
  user2Id: string;
  status: 'incomplete' | 'complete';
  timeStatus: 'live' | 'expired';
  createdAt: Date;
}
```

## Dark Mode Support

All components support dark mode out of the box using `next-themes`.

```tsx
import { ThemeProvider } from 'next-themes';

export function App() {
  return (
    <ThemeProvider attribute="class">
      <YourApp />
    </ThemeProvider>
  );
}
```

## Browser Support

- Chrome (latest)
- Firefox (latest)
- Safari (latest)
- Edge (latest)

## Performance

- ⚡ Tree-shakeable
- 🎯 Only loads used components
- 💨 Optimized bundle size
- 🔧 Minimal dependencies

## Contributing

Contributions welcome! Please follow these steps:

1. Fork the repository
2. Create a feature branch
3. Commit your changes
4. Push to the branch
5. Open a Pull Request

## License

MIT © 2025 ShoutX

## Support

For issues and questions, please open an issue on GitHub.

---

**Made with ❤️ by ShoutX Team**