<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>For You</title>

<style>
/* Reset */
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: 'Georgia', serif;
}

/* Background */
body {
  height: 100vh;
  background: linear-gradient(135deg, #ffdde1, #ee9ca7);
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
}

/* Hidden checkbox */
#open {
  display: none;
}

/* Card container */
.card {
  width: 320px;
  height: 220px;
  background: #fff;
  border-radius: 12px;
  box-shadow: 0 15px 40px rgba(0,0,0,0.2);
  cursor: pointer;
  perspective: 1000px;
  position: relative;
  overflow: hidden;
}

/* Front cover */
.front {
  position: absolute;
  inset: 0;
  background: linear-gradient(135deg, #ff758c, #ff7eb3);
  border-radius: 12px;
  display: flex;
  align-items: center;
  justify-content: center;
  color: #fff;
  font-size: 1.2rem;
  letter-spacing: 1px;
  transition: transform 1s ease;
  transform-origin: left;
  backface-visibility: hidden;
  z-index: 2;
}

/* Letter container */
.letter {
  position: absolute;
  inset: 0;
  padding: 18px;
  color: #444;
  font-size: 0.9rem;
  line-height: 1.5;
  opacity: 0;
  transition: opacity 1s ease 0.6s;
}

/* Pages */
.pages {
  display: flex;
  width: 200%;
  height: 100%;
  transition: transform 0.6s ease;
}

.page {
  width: 50%;
  padding-right: 10px;
}

/* Navigation buttons */
.nav {
  position: absolute;
  bottom: 10px;
  right: 15px;
  font-size: 0.75rem;
  color: #ff758c;
  cursor: pointer;
  user-select: none;
}

.back {
  right: auto;
  left: 15px;
  display: none;
}

/* Open animation */
#open:checked + label .front {
  transform: rotateY(-160deg);
}

#open:checked + label .letter {
  opacity: 1;
}

/* Hint */
.hint {
  margin-top: 15px;
  font-size: 0.8rem;
  color: #555;
}
</style>
</head>

<body>

<input type="checkbox" id="open">

<label for="open">
  <div class="card">

    <div class="front">
      Tap to Open 💌
    </div>

    <div class="letter">
      <div class="pages" id="pages">

        <!-- PAGE 1 -->
        <div class="page">
          <p>
            Hi.<br><br>
            Hi Golo, it’s me again. I know this is a little weird, but  
            I’ve been wanting to tell you that I like you since the very first time I saw you.  
            When I saw your beautiful smile, my heart fluttered—  
            it was one of the most beautiful things I’ve ever seen.
          </p>
        </div>

        <!-- PAGE 2 -->
        <div class="page">
          <p>
            You became one of the best things that ever happened to me.<br><br>
            This isn’t meant to pressure you or expect anything.  
            I just wanted to be honest—because some feelings deserve  
            to be said at least once.<br><br>
            Take care, always.
          </p>
        </div>

      </div>

      <div class="nav back" id="backBtn">← Back</div>
      <div class="nav next" id="nextBtn">Next →</div>
    </div>

  </div>
</label>

<div class="hint">Click the card</div>

<script>
const pages = document.getElementById("pages");
const next = document.getElementById("nextBtn");
const back = document.getElementById("backBtn");

let page = 0;

next.onclick = (e) => {
  e.stopPropagation();
  page = 1;
  pages.style.transform = "translateX(-50%)";
  next.style.display = "none";
  back.style.display = "block";
};

back.onclick = (e) => {
  e.stopPropagation();
  page = 0;
  pages.style.transform = "translateX(0)";
  next.style.display = "block";
  back.style.display = "none";
};
</script>

</body>
</html>

