# README.md

## EventHunter

EventHunter is a React-based web application that allows users to search for events in a specified city using the PredictHQ API.

### Features
- Search events by city
- View event details (title, description, start & end time, duration)
- Redirect to ticket booking
- Responsive UI
- Loading indicator

### Tech Stack
- **Frontend:** React.js
- **Backend:** Node.js, Express.js
- **Database:** None (uses external API)
- **Styling:** CSS, Tailwind CSS
- **Other:** Axios, dotenv, cors

## Setup Instructions

### Prerequisites
- Node.js (>= 14.x)
- npm or yarn

### Installation
1. Clone the repository:
   ```bash
   git clone <repo_url>
   cd event-app
   ```
2. Install dependencies for both client and server:
   ```bash
   cd client
   npm install
   cd ../server
   npm install
   ```

### Environment Setup
Create a `.env` file in the `server` directory and add:
```
PORT=5000
API_TOKEN=your_predictHQ_api_token
```

### Running the Application
Start the server:
```bash
cd server
nodemon index.js
```
Start the client:
```bash
cd client
npm run dev
```

The application will be accessible at `http://localhost:5173` (default Vite port).

---

# Report: EventHunter Project

## Approach
The project follows a **client-server architecture**:
- The **React frontend** provides a search interface where users can enter a city name.
- The **Node.js backend** fetches events from the PredictHQ API and serves them to the frontend.
- **Axios** is used for API communication, and **CORS** ensures cross-origin requests work.
- A modal is used to request the user's Gmail before redirection to the ticket booking page.
- Loader animation enhances the user experience while fetching events.

## Challenges Faced
1. **CORS Issues:** Initially, the PredictHQ API blocked direct requests from the frontend. Solved by routing requests through the Express server.
2. **Data Formatting:** PredictHQ API response contains unnecessary data. Extracted only relevant fields (title, description, start, end, duration).
3. **Loading State:** Without a loader, the UI seemed unresponsive. Implemented `react-loader-spinner` for better UX.

## Improvements & Future Enhancements
- **Pagination:** Currently, all events are loaded at once. Implementing pagination would improve performance.
- **Better Event Filtering:** Adding filters for event type, date, and price range.
- **User Authentication:** Implementing user accounts to save event preferences.
- **Real Ticket Booking:** Instead of redirecting users, integrate with actual ticket providers.

This project demonstrates an effective use of React and Node.js to fetch and display event data efficiently.

