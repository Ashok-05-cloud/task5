# task5
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Ashok | Pro Portfolio</title>

<style>
:root {
    --primary: #00f5c4;
    --bg: #0f172a;
    --glass: rgba(255,255,255,0.08);
}

body {
    margin: 0;
    font-family: 'Poppins', sans-serif;
    background: var(--bg);
    color: white;
    overflow-x: hidden;
}

/* NAVBAR */
nav {
    display: flex;
    justify-content: space-between;
    padding: 20px 50px;
    position: sticky;
    top: 0;
    backdrop-filter: blur(10px);
    background: rgba(0,0,0,0.3);
}

nav h1 {
    color: var(--primary);
}

/* HERO */
.hero {
    text-align: center;
    padding: 100px 20px;
}

.hero h2 {
    font-size: 3rem;
}

.typing {
    color: var(--primary);
    border-right: 2px solid;
    padding-right: 5px;
}

/* PROJECTS */
.projects {
    padding: 50px;
}

.filter {
    text-align: center;
    margin-bottom: 20px;
}

.filter button {
    margin: 5px;
    padding: 8px 15px;
    border: none;
    cursor: pointer;
    background: var(--primary);
    color: black;
}

.grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px,1fr));
    gap: 20px;
}

.card {
    background: var(--glass);
    padding: 20px;
    border-radius: 15px;
    transition: 0.4s;
    backdrop-filter: blur(10px);
}

.card:hover {
    transform: translateY(-10px) scale(1.03);
}

/* CONTACT */
.contact {
    text-align: center;
    padding: 50px;
}

input, textarea {
    width: 80%;
    padding: 12px;
    margin: 10px;
    border-radius: 5px;
    border: none;
}

.error {
    color: red;
}

/* FOOTER */
footer {
    text-align: center;
    padding: 20px;
    opacity: 0.6;
}

/* ANIMATION */
.hidden {
    opacity: 0;
    transform: translateY(50px);
    transition: 1s;
}

.show {
    opacity: 1;
    transform: translateY(0);
}
</style>
</head>

<body>

<nav>
    <h1>Ashok.dev</h1>
</nav>

<section class="hero">
    <h2>I am <span class="typing"></span></h2>
    <p>Frontend Developer | ApexPlanet Intern 🚀</p>
</section>

<section class="projects">
    <div class="filter">
        <button onclick="filterProjects('all')">All</button>
        <button onclick="filterProjects('web')">Web</button>
        <button onclick="filterProjects('js')">JavaScript</button>
    </div>

    <div class="grid">
        <div class="card hidden" data-type="web">
            <h3>Portfolio</h3>
            <p>Responsive portfolio site</p>
        </div>

        <div class="card hidden" data-type="js">
            <h3>Todo App</h3>
            <p>Dynamic JS project</p>
        </div>

        <div class="card hidden" data-type="web">
            <h3>Landing Page</h3>
            <p>Modern UI design</p>
        </div>
    </div>
</section>

<section class="contact">
    <h2>Contact Me</h2>
    <input id="name" placeholder="Your Name"><br>
    <input id="email" placeholder="Your Email"><br>
    <textarea id="msg" placeholder="Message"></textarea><br>
    <button onclick="validate()">Send</button>
    <p id="error" class="error"></p>
</section>

<footer>
    <p>© 2026 Ashok | Built for ApexPlanet Task 5</p>
</footer>

<script>
// TYPING EFFECT
const words = ["Ashok", "Developer", "Problem Solver", "UI Creator"];
let i=0, j=0, currentWord="", isDeleting=false;

function type() {
    currentWord = words[i];
    document.querySelector(".typing").textContent =
        currentWord.substring(0, j);

    if(!isDeleting && j < currentWord.length) j++;
    else if(isDeleting && j > 0) j--;
    else {
        isDeleting = !isDeleting;
        if(!isDeleting) i = (i+1) % words.length;
    }

    setTimeout(type, isDeleting ? 50 : 100);
}
type();

// FILTER PROJECTS
function filterProjects(type) {
    document.querySelectorAll(".card").forEach(card => {
        card.style.display =
            (type === 'all' || card.dataset.type === type)
            ? "block" : "none";
    });
}

// FORM VALIDATION
function validate() {
    let name = document.getElementById("name").value;
    let email = document.getElementById("email").value;
    let msg = document.getElementById("msg").value;

    if(!name || !email || !msg){
        document.getElementById("error").innerText =
            "All fields are required!";
        return;
    }

    document.getElementById("error").innerText =
        "Message sent successfully 🚀";
}

// SCROLL ANIMATION
const observer = new IntersectionObserver(entries => {
    entries.forEach(entry => {
        if(entry.isIntersecting){
            entry.target.classList.add("show");
        }
    });
});

document.querySelectorAll(".hidden").forEach(el => observer.observe(el));

</script>

</body>
</html>
