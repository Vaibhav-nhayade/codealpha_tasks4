const songs = [

  {
    title: "Dreams",
    artist: "Alex Music",
    src: "https://www.soundhelix.com/examples/mp3/SoundHelix-Song-1.mp3"
  },

  {
    title: "Night Drive",
    artist: "John Beats",
    src: "https://www.soundhelix.com/examples/mp3/SoundHelix-Song-2.mp3"
  },

  {
    title: "Summer Vibes",
    artist: "DJ Wave",
    src: "https://www.soundhelix.com/examples/mp3/SoundHelix-Song-3.mp3"
  }

];

const audio = document.getElementById("audio");

const title = document.getElementById("title");

const artist = document.getElementById("artist");

const playBtn = document.getElementById("play");

const prevBtn = document.getElementById("prev");

const nextBtn = document.getElementById("next");

const progress = document.getElementById("progress");

const progressContainer = document.getElementById("progress-container");

const currentTimeEl = document.getElementById("current-time");

const durationEl = document.getElementById("duration");

const volume = document.getElementById("volume");

const playlist = document.getElementById("playlist");

let songIndex = 0;

let isPlaying = false;

// Load Song
function loadSong(song) {

  title.innerText = song.title;

  artist.innerText = song.artist;

  audio.src = song.src;
}

// Play Song
function playSong() {

  isPlaying = true;

  audio.play();

  playBtn.innerHTML =
    '<i class="fa-solid fa-pause"></i>';
}

// Pause Song
function pauseSong() {

  isPlaying = false;

  audio.pause();

  playBtn.innerHTML =
    '<i class="fa-solid fa-play"></i>';
}

// Play / Pause
playBtn.addEventListener("click", () => {

  if (isPlaying) {
    pauseSong();
  }

  else {
    playSong();
  }

});

// Next Song
function nextSong() {

  songIndex++;

  if (songIndex > songs.length - 1) {
    songIndex = 0;
  }

  loadSong(songs[songIndex]);

  playSong();
}

// Previous Song
function prevSong() {

  songIndex--;

  if (songIndex < 0) {
    songIndex = songs.length - 1;
  }

  loadSong(songs[songIndex]);

  playSong();
}

nextBtn.addEventListener("click", nextSong);

prevBtn.addEventListener("click", prevSong);

// Update Progress Bar
audio.addEventListener("timeupdate", updateProgress);

function updateProgress(event) {

  const { duration, currentTime } = event.srcElement;

  const progressPercent =
    (currentTime / duration) * 100;

  progress.style.width = `${progressPercent}%`;

  // Time
  currentTimeEl.innerText =
    formatTime(currentTime);

  durationEl.innerText =
    formatTime(duration);
}

// Format Time
function formatTime(time) {

  const minutes = Math.floor(time / 60);

  let seconds = Math.floor(time % 60);

  if (seconds < 10) {
    seconds = `0${seconds}`;
  }

  return `${minutes}:${seconds}`;
}

// Progress Click
progressContainer.addEventListener("click", setProgress);

function setProgress(event) {

  const width = this.clientWidth;

  const clickX = event.offsetX;

  const duration = audio.duration;

  audio.currentTime =
    (clickX / width) * duration;
}

// Volume Control
volume.addEventListener("input", () => {

  audio.volume = volume.value;
});

// Autoplay Next Song
audio.addEventListener("ended", nextSong);

// Create Playlist
songs.forEach((song, index) => {

  const li = document.createElement("li");

  li.innerText = `${song.title} - ${song.artist}`;

  li.addEventListener("click", () => {

    songIndex = index;

    loadSong(songs[songIndex]);

    playSong();
  });

  playlist.appendChild(li);

});

// Load First Song
loadSong(songs[songIndex]);
