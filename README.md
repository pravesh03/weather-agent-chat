# 🌤️ Weather Agent Chat Application

A modern, responsive weather chat application built with Next.js, React, and TypeScript. This application provides real-time weather information through an AI-powered weather agent with a beautiful, interactive chat interface.

## ✨ Features

- 🤖 **AI Weather Agent**: Powered by Mastra Cloud weather agent
- 💬 **Real-time Chat Interface**: Modern chat UI with message bubbles
- 🌙 **Dark/Light Theme**: Toggle between dark and light modes
- 🔊 **Sound Notifications**: Audio feedback for messages and errors
- 📱 **Responsive Design**: Works perfectly on desktop and mobile
- 📝 **Chat History**: Save and manage multiple conversations
- 🔄 **Retry Mechanism**: Retry failed requests with one click
- 📤 **Export Conversations**: Export chat history as text files
- ⚡ **Streaming Responses**: Real-time streaming of weather data
- 🛡️ **Error Handling**: Comprehensive error handling with user-friendly messages

## 💡 Tips for Success

### Development Best Practices

1. **Start Simple**: Get basic chat functionality working first
   - Begin with a simple message input and display
   - Add streaming responses once basic functionality works
   - Incrementally add features like history, themes, etc.

2. **Read the API**: Understand the request/response format thoroughly
   - Study the API specification carefully
   - Test with curl commands before implementing
   - Handle different response formats (SSE, streaming, JSON)

3. **Test Early**: Test with the actual API as soon as possible
   - Don't wait until the end to test API integration
   - Use browser DevTools to monitor network requests
   - Test error scenarios (network issues, invalid responses)

4. **Focus on UX**: Prioritize user experience over complex features
   - Mobile-first design approach
   - Smooth animations and transitions
   - Clear error messages and loading states
   - Intuitive navigation and interactions

5. **Document Decisions**: Explain your technical choices in the README
   - Why certain libraries were chosen
   - Architecture decisions and trade-offs
   - Mobile optimization strategies
   - Error handling approaches

6. **Handle Errors**: Robust error handling will set you apart
   - Network errors with retry mechanisms
   - User-friendly error messages
   - Graceful degradation when services are unavailable
   - Comprehensive logging for debugging

## 🚀 Quick Start

### Prerequisites

- Node.js 18.0 or later
- npm or yarn package manager

### Installation

1. **Clone the repository**
   ```bash
   git clone <your-repo-url>
   cd weather-agent-chat
   ```

2. **Install dependencies**
   ```bash
   npm install
   # or
   yarn install
   ```

3. **Start the development server**
   ```bash
   npm run dev
   # or
   yarn dev
   ```

4. **Open your browser**
   Navigate to [http://localhost:3000](http://localhost:3000)

## 🛠️ Development

### Available Scripts

- `npm run dev` - Start development server
- `npm run build` - Build for production
- `npm run start` - Start production server
- `npm run lint` - Run ESLint

### Project Structure

```
weather-agent-chat/
├── app/                    # Next.js app directory
│   ├── globals.css        # Global styles
│   ├── layout.tsx         # Root layout
│   └── page.tsx          # Home page
├── components/            # React components
│   ├── ChatInput.tsx     # Message input component
│   ├── ChatWindow.tsx   # Main chat interface
│   ├── MessageBubble.tsx # Individual message display
│   ├── SearchHistory.tsx # Conversation history
│   ├── ExportButton.tsx  # Export functionality
│   ├── Loader.tsx        # Loading animations
│   ├── SoundToggle.tsx   # Sound control
│   └── ThemeToggle.tsx   # Theme switcher
├── contexts/             # React contexts
│   └── SoundContext.tsx  # Sound management
├── hooks/                # Custom React hooks
│   ├── useWeatherChat.ts # Main chat logic
│   └── useSoundNotification.ts # Sound notifications
├── public/               # Static assets
├── package.json          # Dependencies and scripts
├── tailwind.config.js    # Tailwind CSS configuration
├── tsconfig.json         # TypeScript configuration
└── next.config.js        # Next.js configuration
```

## 📱 Mobile-First Design

### Design Philosophy

This application follows a **mobile-first approach**, ensuring optimal performance and user experience across all devices, from smartphones to desktop computers.

### Mobile Optimizations

#### **Touch Interactions**
- **44px minimum touch targets**: All interactive elements meet accessibility guidelines
- **Touch manipulation**: Optimized touch actions for better scrolling and interaction
- **Visual feedback**: Active states with `active:scale-95` for immediate user feedback
- **Tap highlight removal**: Clean touch interactions without browser highlights

#### **Responsive Layout**
- **Full-screen mobile sidebar**: History panel overlays entire screen on mobile
- **Auto-closing sidebar**: Automatically closes after conversation selection
- **Dynamic viewport height**: Uses `100dvh` for proper mobile viewport handling
- **Safe area support**: Handles device notches and rounded corners

#### **Performance Optimizations**
- **Font size optimization**: 16px minimum to prevent iOS zoom on input focus
- **Horizontal scroll prevention**: Prevents unwanted horizontal scrolling
- **Smooth animations**: Optimized transitions for mobile performance
- **Memory efficient**: Proper cleanup and resource management

#### **User Experience**
- **Larger text on mobile**: Better readability with optimized font sizes
- **Improved spacing**: Mobile-optimized padding and margins
- **Better message bubbles**: Optimized width and spacing for mobile screens
- **Touch-friendly buttons**: Larger touch targets with proper spacing

### Technical Implementation

```css
/* Mobile-specific CSS utilities */
.touch-manipulation {
  touch-action: manipulation;
}

.mobile-safe-area {
  padding-left: env(safe-area-inset-left);
  padding-right: env(safe-area-inset-right);
  padding-top: env(safe-area-inset-top);
  padding-bottom: env(safe-area-inset-bottom);
}

.mobile-viewport {
  min-height: 100vh;
  min-height: 100dvh; /* Dynamic viewport height */
}
```

## 🔧 Configuration

### API Configuration

The application is configured to use the Mastra Cloud weather agent API:

```typescript
// hooks/useWeatherChat.ts
const API_URL = 'https://millions-screeching-vultur.mastra.cloud/api/agents/weatherAgent/stream'
const THREAD_ID = '60002220086' // Your college roll number
```

### Environment Variables (Optional)

Create a `.env.local` file for custom configuration:

```env
NEXT_PUBLIC_API_URL=your_custom_api_url
NEXT_PUBLIC_THREAD_ID=your_thread_id
```

## 🏗️ Technical Architecture

### Design Decisions

#### **Framework Choice: Next.js 14**
- **App Router**: Modern routing system with better performance
- **Server Components**: Improved SEO and initial load times
- **Built-in optimizations**: Image optimization, font loading, etc.
- **TypeScript support**: Type safety and better developer experience

#### **Styling: Tailwind CSS**
- **Utility-first approach**: Rapid development and consistent design
- **Mobile-first responsive design**: Built-in responsive utilities
- **Custom CSS variables**: Theme system with CSS custom properties
- **Performance**: Purged CSS for optimal bundle size

#### **State Management: React Hooks**
- **Custom hooks**: `useWeatherChat` for chat logic, `useSound` for audio
- **Context API**: Sound preferences and theme management
- **Local state**: Component-level state with useState and useRef
- **No external state library**: Keeps bundle size minimal

#### **API Integration Strategy**
- **Streaming responses**: Real-time weather data updates
- **Multiple format support**: Handles SSE, direct streaming, and JSON
- **Error handling**: Comprehensive error states with retry mechanisms
- **Timeout management**: 45-second timeout with proper cleanup

#### **Mobile-First Approach**
- **Touch optimization**: `touch-action: manipulation` for better scrolling
- **Viewport handling**: Dynamic viewport height (`100dvh`) support
- **Safe area support**: Handles device notches and rounded corners
- **Accessibility**: 44px minimum touch targets

### Error Handling Strategy

#### **Network Errors**
- **Retry mechanism**: One-click retry for failed requests
- **Timeout handling**: 45-second timeout with user feedback
- **Graceful degradation**: Fallback messages when API is unavailable
- **User-friendly messages**: Clear, actionable error descriptions

#### **Input Validation**
- **Message length limits**: 1000 character maximum
- **Empty message prevention**: Disabled send button for empty inputs
- **Special character support**: Proper handling of Unicode characters
- **Real-time validation**: Immediate feedback on input issues

#### **API Response Handling**
- **Multiple format parsing**: SSE, streaming, and JSON responses
- **Metadata filtering**: Removes technical metadata from user display
- **Content validation**: Ensures actual content is received
- **Fallback responses**: Default messages when no content is received

## 🎨 Customization

### Styling

The application uses Tailwind CSS for styling. Key customization files:

- `app/globals.css` - Global styles and CSS variables
- `tailwind.config.js` - Tailwind configuration
- Component files - Individual component styles

### Themes

The application supports both dark and light themes. Theme colors are defined in `globals.css`:

```css
:root {
  --primary-50: #eff6ff;
  --primary-500: #3b82f6;
  --primary-900: #1e3a8a;
  /* ... more color variables */
}
```

## 📚 Development Process

### Implementation Timeline

1. **Phase 1: Basic Setup**
   - Next.js project initialization
   - Tailwind CSS configuration
   - Basic component structure
   - API endpoint configuration

2. **Phase 2: Core Functionality**
   - Chat input and message display
   - API integration with streaming responses
   - Basic error handling
   - Conversation management

3. **Phase 3: User Experience**
   - Theme toggle (dark/light mode)
   - Sound notifications
   - Chat history sidebar
   - Export functionality

4. **Phase 4: Mobile Optimization**
   - Mobile-first responsive design
   - Touch interaction improvements
   - Safe area support
   - Performance optimizations

5. **Phase 5: Error Handling & Polish**
   - Comprehensive error handling
   - Retry mechanisms
   - Loading states
   - User feedback improvements

### Key Challenges & Solutions

#### **Challenge: First Request Not Working**
**Problem**: Messages appeared to be "lost" on the first request
**Solution**: Fixed conversation ID generation to ensure consistency between user messages and API responses

#### **Challenge: API Response Parsing**
**Problem**: Raw metadata was being displayed to users
**Solution**: Implemented comprehensive response parsing to filter out technical metadata and display only user-facing content

#### **Challenge: Mobile Experience**
**Problem**: Poor mobile usability and touch interactions
**Solution**: Implemented mobile-first design with touch optimizations, safe area support, and responsive layouts

#### **Challenge: Error Handling**
**Problem**: Generic error messages didn't help users
**Solution**: Created specific error messages with actionable solutions and retry mechanisms

### Lessons Learned

1. **Test API Integration Early**: Don't wait until the end to test with real API responses
2. **Mobile-First Design**: Start with mobile constraints and enhance for desktop
3. **Error Handling is Critical**: Users need clear, actionable error messages
4. **Streaming Responses Require Careful Parsing**: Multiple response formats need robust handling
5. **Touch Interactions Matter**: Mobile users need immediate visual feedback
6. **Documentation Saves Time**: Well-documented code and decisions help with debugging and maintenance

## 🧪 Testing

### Manual Testing

Test the application with these scenarios:

1. **Basic Interaction**
   - Send: "What's the weather in London?"
   - Verify clean response without metadata

2. **Error Handling**
   - Disconnect internet and send message
   - Verify error message and retry functionality

3. **Multiple Messages**
   - Send several weather queries
   - Verify conversation flow

4. **Edge Cases**
   - Very long messages (should be blocked)
   - Empty messages (should be ignored)
   - Special characters (should work)

### API Testing

Test the API directly with curl:

```bash
curl -X POST "https://millions-screeching-vultur.mastra.cloud/api/agents/weatherAgent/stream" \
  -H "x-mastra-dev-playground: true" \
  -H "Content-Type: application/json" \
  -d '{
    "messages": [{"role": "user", "content": "What is the weather in London?"}],
    "runId": "weatherAgent",
    "maxRetries": 2,
    "maxSteps": 5,
    "temperature": 0.5,
    "topP": 1,
    "runtimeContext": {},
    "threadId": "60002220086",
    "resourceId": "weatherAgent"
  }'
```

## 🚀 Deployment

### Vercel (Recommended)

1. Push your code to GitHub
2. Connect your repository to Vercel
3. Deploy automatically

### Other Platforms

The application can be deployed to any platform that supports Next.js:

- Netlify
- AWS Amplify
- Railway
- Heroku

### Build for Production

```bash
npm run build
npm run start
```

## 🔍 Troubleshooting

### Common Issues

1. **API Not Found Error**
   - Verify the API endpoint is correct
   - Check if the Mastra Cloud service is running

2. **First Request Not Working**
   - Check browser console for errors
   - Verify conversation ID generation

3. **Styling Issues**
   - Ensure Tailwind CSS is properly configured
   - Check if all dependencies are installed

4. **Sound Not Working**
   - Check browser audio permissions
   - Verify sound files are accessible

### Debug Mode

Enable debug logging by checking the browser console. The application logs:

- API requests and responses
- Conversation state changes
- Error details
- Streaming data processing

## 📚 API Documentation

### Request Format

```typescript
{
  "messages": [{"role": "user", "content": "Your message"}],
  "runId": "weatherAgent",
  "maxRetries": 2,
  "maxSteps": 5,
  "temperature": 0.5,
  "topP": 1,
  "runtimeContext": {},
  "threadId": "60002220086",
  "resourceId": "weatherAgent"
}
```

### Response Format

The API returns streaming data in multiple formats:

- SSE format: `data: {"type": "text", "content": "..."}`
- Direct streaming: `0:"text content"`
- Metadata: `f:{"messageId": "..."}`

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test thoroughly
5. Submit a pull request

## 📄 License

This project is licensed under the MIT License.

## 🙏 Acknowledgments

- Mastra Cloud for the weather agent API
- Next.js team for the amazing framework
- Tailwind CSS for the utility-first CSS framework
- React team for the component library

## 📞 Support

If you encounter any issues or have questions:

1. Check the troubleshooting section
2. Review the browser console for errors
3. Test the API directly with curl
4. Create an issue in the repository

---

**Happy Weather Chatting! 🌤️**