# Echo Chamber Buster - Interaction Design

## Core Interaction Flow

### 1. Initial Load & Topic Generation
- **Trigger**: User opens the application
- **Action**: App detects fresh session via sessionStorage
- **Response**: AI generates a random controversial topic from 8 domains
- **Display**: Topic appears as first message with subtle animation
- **Domains**: Life/Existence, Ethics/Morality, Rights/Justice, Traditions/Culture, Society/Politics, Science/Philosophy, Psychology/Behavior, Environment/Technology

### 2. User Engagement Loop
- **Input**: User shares their perspective on the controversial topic
- **Processing**: App sends user input + conversation history to Gemini API
- **AI Response**: Adversarial AI generates counter-arguments using:
  - Direct opposition to user's points
  - Citations from historical figures (Socrates, Nietzsche, MLK Jr., Gandhi, Einstein, Freud)
  - References to spiritual texts (Bhagavad Gita, Bible, Quran, Tao Te Ching, Upanishads)
  - Scientific research and data (Kahneman, Milgram, WHO, IPCC)
- **Display**: AI response appears with typing animation

### 3. Multi-Turn Debate Cycle
- **Continuation**: User responds to AI's counter-arguments
- **Escalation**: AI references previous exchanges to expose inconsistencies
- **Pattern**: Every 3rd AI response includes humility reminder about absolute truth
- **Persistence**: Full conversation history maintained for context

### 4. Session Conclusion
- **Surrender Detection**: App recognizes phrases like "I give up", "You're right", "Enough"
- **Graceful Exit**: AI responds with encouraging message about wisdom of uncertainty
- **Reset**: New chat button clears session and generates fresh topic

## UI Interaction Elements

### Sidebar Interactions
- **New Chat Button**: Clears current session, generates new topic
- **History List**: Shows last 5 conversation topics (clickable to review)
- **Theme Toggle**: Switches between light/dark modes
- **Mobile**: Hamburger menu collapses sidebar

### Main Chat Area
- **Message Input**: Auto-resizing textarea, Enter key submission
- **Send Button**: Disabled when empty, shows loading state during API calls
- **Typing Indicator**: Animated dots when AI is generating response
- **Message Bubbles**: User (right, blue), AI (left, gray) with smooth fade-in

### Error Handling
- **API Failures**: Shows "Connection hiccup—retrying..." with retry logic
- **Rate Limits**: Exponential backoff (1s, 2s, 4s delays)
- **Offline Mode**: Graceful degradation with cached content

## Technical Interactions

### State Management
- **sessionStorage**: Tracks current conversation
- **localStorage**: Persists last 5 conversation histories
- **Memory**: Maintains conversation array for API context

### API Integration
- **Gemini Endpoint**: Async POST requests with conversation history
- **Safety Settings**: Medium+ blocking for harmful content
- **Prompt Engineering**: Dynamic prompts based on conversation state
- **Response Streaming**: Batch processing with typing simulation

### Mobile Responsiveness
- **Touch Events**: Optimized for mobile interaction
- **Keyboard**: Proper viewport handling for input fields
- **Gestures**: Swipe-friendly sidebar toggle