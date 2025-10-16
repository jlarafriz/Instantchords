import { db, auth } from "./firebase.js";
import {
  collection,
  getDocs,
  addDoc
} from "https://www.gstatic.com/firebasejs/10.12.2/firebase-firestore.js";
import {
  signInWithEmailAndPassword,
  onAuthStateChanged
} from "https://www.gstatic.com/firebasejs/10.12.2/firebase-auth.js";

const loginBtn = document.getElementById("login-btn");
const songsSection = document.getElementById("songs-section");
const loginSection = document.getElementById("login-section");
const songsList = document.getElementById("songs-list");
const errorMsg = document.getElementById("login-error");

if (loginBtn) {
  loginBtn.addEventListener("click", async () => {
    const email = document.getElementById("email").value;
    const password = document.getElementById("password").value;
    try {
      await signInWithEmailAndPassword(auth, email, password);
    } catch (err) {
      errorMsg.textContent = "Error al iniciar sesión";
    }
  });
}

onAuthStateChanged(auth, async (user) => {
  if (user) {
    loginSection?.classList.add("hidden");
    songsSection?.classList.remove("hidden");

    const songsSnapshot = await getDocs(collection(db, "songs"));
    songsList.innerHTML = "";
    songsSnapshot.forEach((doc) => {
      const song = doc.data();
      const li = document.createElement("li");
      li.innerHTML = `<strong>${song.title}</strong> - ${song.author}`;
      songsList.appendChild(li);
    });
  }
});
