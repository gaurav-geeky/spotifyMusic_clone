# js play code 

async function getSongs() {
    let a = await fetch("http://127.0.0.1:5500/songs/");
    let response = await a.text();

    let div = document.createElement("div");
    div.innerHTML = response;
    let as = div.getElementsByTagName("a");

    let songs = [];

    for (let index = 0; index < as.length; index++) {
        let element = as[index];
        if (element.href.endsWith(".mp3")) {
            songs.push(element.href);
        }
    }
    return songs;
}

async function main() {
    // get the list of all songs
    let songs = await getSongs();
    console.log(songs);

    // Add a button or use existing play button
    const playButton = document.querySelector('.play svg');

    playButton.addEventListener('click', () => {
        let audio = new Audio(songs[0]);
        audio.play()
            .then(() => console.log("Playing:", songs[0]))
            .catch(err => console.error("Playback error:", err));
    });
}

main();


# In Chrome:

Visit: chrome://settings/content/sound

Toggle “Allow sites to play sound”

Or, allow your localhost site manually. 









// 
2: 11 pe 
new js lagegi so old one .... 


console.log('Lets write javascript');

async function getSongs() {
    let a = await fetch("http://127.0.0.1:5500/songs/");
    let response = await a.text();

    let div = document.createElement("div");
    div.innerHTML = response;
    let as = div.getElementsByTagName("a");

    let songs = [];

    for (let index = 0; index < as.length; index++) {
        let element = as[index];
        if (element.href.endsWith(".mp3")) {
            songs.push(element.href.split("/songs/")[1]);
        }
    }
    return songs;
}

async function main() {
    // get the list of all songs .. .. 
    let songs = await getSongs();

    // show all songs in playlist..
    let songUL = document.querySelector(".songList").getElementsByTagName("ul")[0];
    for (const song of songs) {
        songUL.innerHTML = songUL.innerHTML + `<li> ${song.replaceAll("%20", " ")} </li>`;
    }
    let playButton = document.querySelector('img[src="play.svg"]');

    playButton.addEventListener('click', () => {

        // let audio = new Audio(songs[0]);
        let audio = new Audio("http://127.0.0.1:5500/songs/" + songs[0]);


        // Wait for metadata to load before accessing duration
        audio.addEventListener('loadedmetadata', () => {
            console.log("Duration:", audio.duration.toFixed(2), "seconds");
            console.log("Current src:", audio.currentSrc,);
            console.log("Current Time:", audio.currentTime,);
        });

        audio.play()
            .then(() => console.log("Playing:", songs[1]))
            .catch(err => console.error("Playback error:", err));
    });

}

main();


