# CashFlux 💸

"CashFlux" is a personal finance application designed to help users keep detailed track of their income and expenses. The app allows users to add, view, and delete financial transactions, providing a clear and organized view of their financial history. Additionally, it offers interactive charts to help understand financial trends over time.

> **Note:** This application is designed for mobile devices and does not have a desktop version.

## Main Features 🚀

- **Movements Component**: Displays all recorded financial transactions with details such as title, description, and amount.
- **Movement Subcomponent**: Renders each individual transaction with a clear and attractive layout, including a delete button.
- **Action Component**: Provides a modal form for users to add new financial transactions. Users can enter a title, amount, description, and specify whether it's an income or an expense. The new transaction is added to the list and saved in localStorage.
- **Delete Functionality**: Each transaction includes an option to be deleted. Clicking the delete button triggers an event that updates the app state, removing the transaction from the list and from localStorage.
- **Graphic Component**: Displays an interactive line chart representing financial transactions over the last 30 days. Users can select specific points to see additional details about corresponding transactions. Interaction is handled via touch events for a smooth user experience.
- **Resume Component**: Presents a summary of the user's financial status, including total savings. This component uses slots to integrate additional charts and actions, allowing flexible customization.
- **localStorage Usage**: All financial transactions are saved in localStorage to ensure data persists between sessions. When the app loads, it retrieves data from localStorage and displays it in the interface.
- **SplashScreen Component**: Shows a loading screen when the app starts, displaying the "CashFlux" logo and title. This screen improves the user experience by providing a smooth transition while the main components load asynchronously.

## Technologies Used 🛠️
- **Vue 3**: Main framework for building the user interface.
- **localStorage**: Used for data persistence between sessions.

## Screenshots 📸

<div align="center">
  <img src="https://i.ibb.co/9nxSWtn/c1.png" alt="Screenshot 1" width="300"/>
  <img src="https://i.ibb.co/9HWYfBp/c2.png" alt="Screenshot 2" width="300"/>
</div>

---

**Take a look 👉🏼 [Cash Flux](https://cash-flux.netlify.app/)**
