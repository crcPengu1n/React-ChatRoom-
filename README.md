# **BadgerChat (Mobile) - A React Native Chat Application**

## **1. Introduction**
Welcome to **BadgerChat (Mobile)**!  
This is a **fully functional mobile chat application**, designed using **React Native** and **Expo**, with secure authentication and real-time chatroom features.

**Key Features:**
- **User Authentication:** Register and log in with a secure PIN.
- **Chatroom Management:** Browse, create, and manage chat messages dynamically.
- **Real-time Messaging:** Pull-to-refresh functionality for instant message updates.
- **Secure Token Storage:** JWT authentication using **expo-secure-store**.
- **Guest Access Mode:** Browse chatrooms without an account.

This project highlights the power of **React Native** in mobile app development, combining **REST APIs, Secure Storage, and Smooth Navigation**.

---

## **2. Features Overview**
### **Secure Login & Registration**
- **Register** with a **username** and **7-digit PIN**.
- **Real-time validation** ensures:
  - "Please enter a PIN" when a PIN is missing.
  - "Pins do not match" when PINs are inconsistent.
  - "A PIN must be exactly 7 digits" when the format is incorrect.
- Securely **stores JWT tokens** with expo-secure-store.

**Example Login Flow**:
[Login Screen] User: "Enter username & PIN" App: "Welcome back, badgerFan!"

---

### **Dynamic Chatroom Management**
- **View all available chatrooms**, dynamically retrieved from the API.
- Uses **React Navigation Drawer** for easy chatroom switching.
- Implements **FlatList pull-to-refresh** for real-time message updates.

**Example Chatroom View**:
[Union South Socials]

Alice: "Game night at 7PM!"
Bob: "See you there!"

---

### **Creating & Posting Messages**
- Users can **create posts** inside chatrooms using a **modal interface**.
- Requires **both a title & message content** (button disabled otherwise).
- Shows a **confirmation alert** when the post is successfully created.

**Example Post Creation**:
> **User:** "Create a post in Lakeshore Lounge"  
> **App:** "Enter title & content"  
> **User:** "Title: Game Night!"  
> **User:** "Content: Who wants to join for board games at 7PM?"  
> **App:** "Post successfully created!"  

---

### ** Deleting Posts**
- Users **can delete their own posts**, but **not others' posts**.
- **Deletes instantly** from the UI with a confirmation alert.

**Example Post Deletion**:
> **User:** "Delete my post in Lakeshore Lounge"  
> **App:** "Post successfully deleted!"  

---

### ** Secure Logout**
- Removes JWT from **expo-secure-store**.
- **Redirects to login screen** after logout.

**Example Logout**:
> **User:** "Log out"  
> **App:** "You have been logged out."  

---

### **Guest Mode (Anonymous Access)**
- Users can **browse chatrooms as guests**.
- **Cannot create posts** unless logged in.
- Instead of logging out, guests **are redirected to sign up**.

**Example Guest Mode**:
> **User:** "Continue as guest"  
> **App:** "You are now browsing as a guest."  

---

## **3. API Integration**
### **API Endpoints**
All API routes are relative to:

`https://cs571api.cs.wisc.edu/rest/f24/hw9/`
| Method | URL                         | Purpose                     | Return Codes      |
|--------|-----------------------------|-----------------------------|-------------------|
| GET    | /chatrooms                  | Retrieve all chatrooms.     | 200, 304          |
| GET    | /messages?chatroom=NAME    | Retrieve messages for a chatroom. | 200, 404 |
| POST   | /messages?chatroom=NAME    | Create a new post.          | 200, 400, 404, 413|
| DELETE | /messages?id=ID            | Delete a post.              | 200, 400, 401, 404|
| POST   | /register                  | Register a new user.        | 200, 400, 409, 413|
| POST   | /login                     | Log in a user.              | 200, 400, 401     |
| GET    | /whoami                    | Get details of the current user. | 200         |

4. How It Works
🛠️ App Structure
- Uses React Navigation for screen transitions.
- Implements JWT-based authentication.
- Uses FlatList for efficient rendering.

Security Measures
- PINs are masked (e.g., "*******").
- Tokens are securely stored using expo-secure-store.
- Restricts unauthorized actions (e.g., only post owners can delete).

UI Enhancements
- Pull-to-refresh in chatrooms.
- Auto-updating message board.
- Intuitive navigation drawer.

5. Installation & Setup
Getting Started
To run the project locally:

```sh
npm install
npm start
```

' Running on a Mobile Device

' Download the Expo Go app on iOS or Android.
' Scan the QR Code from the terminal output.
' Alternatively, use an Android Emulator (AVD).

' Do NOT test in a web browser! This is a mobile-only application.
