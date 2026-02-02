<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>For You</title>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: Georgia, serif;
}

body {
  height: 100vh;
  background: linear-gradient(135deg, #ffdde1, #ee9ca7);
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
}

#open {
  display: none;
}

/* Card */
.card {
  width: 320px;
  height: 200px;
  background: #fff;
  border-radius: 14px;
  box-shadow: 0 15px 40px rgba(0,0,0,0.25);
  position: relative;
  perspective: 1200px;
  transition: height 0.8s ease;
  overflow: hidden;
}

/* Expand card when opened */
#open:checked + label .card {
  height: 360px;
}

/* Front */
.front {
  position: absolute;
  inset: 0;
  background: linear-gradient(135deg, #ff758c, #ff7eb3);
  border-radius: 14px;
  display: flex;
  align-items: center;
  justify-content: center;
  color: white;
  font-size: 1.2rem;
  transition: transform 1s ease;
  transform-origin: left;
  backface-visibility: hidden;
  z-index: 2;
}

/* Letter */
.letter {
  position: absolute;
  inset: 0;
  padding: 22px;
  font-size: 0.95rem;
  line-height: 1.6;
  color: #444;
  opacity: 0;
  transition: opacity 0.6s ease 0.5s;
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
}

/* Buttons */
.nav {
  position: absolute;
  bottom: 14px;
  font-size: 0.8rem;
  color: #ff758c;
  cursor: pointer;
  user-select: none;
}

.next {
  right: 20px;
}

.back {
  left: 20px;
  display: none;
}

/* Open animation */
#open:checked + label .front {
  transform: rotateY(-160deg);
}

#open:checked + label .letter {
  opacity: 1;
}

.hint {
  margin-top: 14px;
  font-size: 0.8rem;
  color: #555;
}
</style>
</head>

<body>

<input type="checkbox" id="open">

<label for="open">
  <div class="card">

    <div class="front">Tap to Open 💌</div>

    <div class="letter">
      <div class="pages" id="pages">

        <div class="page">
          <p>
            Hi.<br><br>
            Hi Golo, it’s me again. I know this is a little weird, but  
            I’ve been wanting to tell you that I like you since the very first time I saw you.  
            When I saw your beautiful smile, my heart fluttered—it was one of the most beautiful
            things I’ve ever seen.
          </p>
        </div>

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

      <div class="nav back" id="back">← Back</div>
      <div class="nav next" id="next">Next →</div>
    </div>

  </div>
</label>

<div class="hint">Click the card</div>

<script>
const pages = document.getElementById("pages");
const next = document.getElementById("next");
const back = document.getElementById("back");

next.onclick = (e) => {
  e.stopPropagation();
  pages.style.transform = "translateX(-50%)";
  next.style.display = "none";
  back.style.display = "block";
};

back.onclick = (e) => {
  e.stopPropagation();
  pages.style.transform = "translateX(0)";
  next.style.display = "block";
  back.style.display = "none";
};
</script>

</body>
</html>
