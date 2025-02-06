# README.md

## EventHunter

EventHunter is a React-based web application that allows users to search for events in a specified city using the PredictHQ API. The application provides a user-friendly interface for discovering local events and seamlessly redirects users to ticket booking pages.

### Features
- **Search events by city:** Users can enter a city name to fetch event listings.
- **View event details:** Displays event title, description, start & end time, and duration.
- **Redirect to ticket booking:** Users can access ticket booking links.
- **Responsive UI:** Ensures accessibility on different screen sizes.
- **Loading indicator:** Provides feedback while events are being fetched.
- **Gmail modal request:** Users are prompted to enter their Gmail before redirection.

### Tech Stack
- **Frontend:** React.js
- **Backend:** Node.js, Express.js
- **Database:** None (uses external API)
- **Styling:** CSS, Tailwind CSS
- **Other:** Axios, dotenv, cors

---

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
Create a `.env` file in the server directory and add:

```env
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

The application will be accessible at [http://localhost:5173](http://localhost:5173) (default Vite port).

---

# Report: EventHunter Project

## Approach
The project follows a **client-server architecture**, which ensures a clear separation between the frontend and backend layers.

### **Frontend (React.js)**
- The user interface is built using **React.js**, ensuring a dynamic and responsive experience.
- A **search bar** allows users to enter a city name and fetch event data from the backend.
- **Axios** is used to send requests to the Node.js server.
- The UI is styled with **Tailwind CSS** for a clean and modern design.
- **React modal** is used to prompt users to enter their Gmail before ticket redirection.
- A **loading spinner** is implemented using `react-loader-spinner` for better user feedback.

### **Backend (Node.js + Express.js)**
- A RESTful API is built using **Express.js** to fetch event data from PredictHQ.
- The backend acts as a proxy server to handle **CORS issues** when communicating with PredictHQ.
- The response is formatted to include only **relevant event details** before being sent to the frontend.

### **External API (PredictHQ)**
- The backend retrieves event data using the **PredictHQ API**, filtering unnecessary fields.
- Users can view event details like **title, description, start & end time, duration, and booking links**.
- Only events with valid booking URLs are displayed.

---

## Challenges Faced & Solutions

1. **CORS Issues**
   - Issue: Direct requests from the frontend were blocked by the PredictHQ API due to **CORS policy**.
   - Solution: Implemented an **Express.js proxy server** to route API calls through the backend, resolving cross-origin request issues.

2. **Data Formatting**
   - Issue: The PredictHQ API returned a large dataset with redundant fields.
   - Solution: Extracted only **title, description, start time, end time, duration, and ticket URL** for improved efficiency and clarity.

3. **Loading State**
   - Issue: Without a loading indicator, users were unsure if the app was fetching data.
   - Solution: Implemented `react-loader-spinner` to display a loading animation while the API request is processed.

4. **Gmail Modal Implementation**
   - Issue: Some users were redirected without providing contact information.
   - Solution: Added a **modal popup** that prompts users to enter their Gmail before ticket redirection.

5. **Event Booking Redirection**
   - Issue: Initially, users were not redirected to valid ticketing platforms.
   - Solution: Filtered events that contain valid **ticket booking URLs**, ensuring only bookable events are shown.

---

## Improvements & Future Enhancements

1. **Pagination Implementation**
   - Currently, all events are fetched and displayed at once, which can affect performance.
   - Implementing **pagination** will improve efficiency and load times.

2. **Advanced Event Filtering**
   - Adding filters for **event type, date range, price range, and location proximity**.
   - This will allow users to find events more relevant to their interests.

3. **User Authentication & Profiles**
   - Implementing **user accounts** to save preferences and past searches.
   - Users can bookmark events and receive personalized recommendations.

4. **Real Ticket Booking Integration**
   - Instead of simply redirecting users, integrating with **ticket providers like Eventbrite or Ticketmaster**.
   - This will allow users to book tickets directly within the app.

5. **Enhanced UI/UX Design**
   - Adding **dark mode** support for better usability.
   - Implementing **animations and interactive elements** for a more engaging experience.

6. **Mobile App Development**
   - Expanding the project to a **React Native mobile app**.
   - This will allow users to find and book events on the go.

---

## Conclusion
EventHunter is a scalable and efficient event search application built using **React and Node.js**. It provides a seamless user experience, allowing users to discover and book events in their city effortlessly. The project showcases **best practices in API integration, UI/UX design, and client-server communication**.

With planned **future enhancements**, EventHunter has the potential to become a **fully-fledged event discovery platform** with robust filtering, authentication, and ticket booking features.

