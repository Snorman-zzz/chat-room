# Chatroom

A simple WebSocket-based chatroom application built with Spring Boot. This project demonstrates how to use Spring Boot and WebSockets to build a real-time chat application with a clean and responsive user interface.

## Features

- **Real-Time Chat:** Users can send messages in real time.
- **Multiple Sessions:** Supports multiple sessions per user (e.g., multiple browser tabs).
- **Online User Count:** Displays the current number of connected users.
- **WebSocket Communication:** Uses a WebSocket server endpoint to broadcast messages.
- **Simple UI:** Built using Thymeleaf and MDUI for a responsive and modern design.

## Requirements

- **Java:** JDK 8 or above.
- **Maven:** For building and running the application.

## Installation

1. **Clone the Repository:**

   ```bash
   git clone https://github.com/yourusername/chatroom.git
   cd chatroom
   ```

2. **Build the Project:**

   ```bash
   mvn clean install
   ```

## Running the Application

Run the application using Maven with the following command:

```bash
mvn spring-boot:run -Dspring-boot.run.jvmArguments="--add-opens java.base/java.lang=ALL-UNNAMED"
```

> **Note:** By default, the application runs on port **9090**. Open your browser and navigate to:
> 
> ```
> http://localhost:9090
> ```
>
> If you prefer to run on port **8080**, update your `application.properties` file:
> 
> ```properties
> server.port=8080
> ```

## Application Structure

- **WebSocketChatApplication.java:**  
  The main class that starts the Spring Boot application and defines routes for the login and chat pages.

- **Message.java:**  
  The model representing a chat message. It includes the username, message content, online user count, and message type.

- **WebSocketChatServer.java:**  
  Implements the WebSocket server endpoint. It handles user connections, broadcasts messages, and updates the online user count.

- **WebSocketConfig.java:**  
  Configures the WebSocket endpoint using Spring’s `ServerEndpointExporter`.

- **chat.html & login.html:**  
  Thymeleaf templates that provide the user interface for the chatroom and login page.

## Usage

1. **Login:**
   - Open the application in your browser.
   - Enter your username on the login page and click "Login" or press Enter.

2. **Chat:**
   - After logging in, you will be directed to the chatroom page.
   - Type your message in the text field and click the "Send (Enter)" button or press Enter.
   - Your message will be broadcast to all connected users, and the online user count is updated in real time.

3. **UI Components:**
   - **Content:** A display chip that labels the area where chat messages appear.
   - **Online Users:** A display chip that shows the current count of connected users.
   - These elements are used for display purposes only and are not interactive.

## Troubleshooting

- **No Messages Displayed:**
  - Ensure the WebSocket URL in `chat.html` is correct and matches the server port.
  - Verify that the client is checking for the correct message type (i.e., `"CHAT"`) in the received JSON.
  - Check the browser console for any errors or issues.

- **Port Issues:**
  - If your server runs on a port other than the one specified in `chat.html`, update the WebSocket URL accordingly.
  - Alternatively, set the desired port in `application.properties` using `server.port`.

- **JVM Module Access Issues:**
  - If you encounter reflective access issues, ensure you pass the correct JVM arguments via Maven as shown above.
