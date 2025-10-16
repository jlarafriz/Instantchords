// Importar funciones necesarias
import { initializeApp } from "https://www.gstatic.com/firebasejs/10.12.2/firebase-app.js";
import { getFirestore } from "https://www.gstatic.com/firebasejs/10.12.2/firebase-firestore.js";
import { getAuth } from "https://www.gstatic.com/firebasejs/10.12.2/firebase-auth.js";

// Configuración del proyecto InstantChords
const firebaseConfig = {
  apiKey: "AIzaSyCDNpKmZQnWzoZ2MKyisp0kJ4CrRo6FGVg",
  authDomain: "instantchords.firebaseapp.com",
  projectId: "instantchords",
  storageBucket: "instantchords.firebasestorage.app",
  messagingSenderId: "692781576341",
  appId: "1:692781576341:web:c39795565277e49f9eeb9c"
};

// Inicializar Firebase
export const app = initializeApp(firebaseConfig);
export const db = getFirestore(app);
export const auth = getAuth(app);
