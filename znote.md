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




volume svg 
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 640 640"><!--!Font Awesome Free v7.1.0 by @fontawesome - https://fontawesome.com License - https://fontawesome.com/license/free Copyright 2025 Fonticons, Inc.--><path fill="#28292a" d="M533.6 96.5C523.3 88.1 508.2 89.7 499.8 100C491.4 110.3 493 125.4 503.3 133.8C557.5 177.8 592 244.8 592 320C592 395.2 557.5 462.2 503.3 506.3C493 514.7 491.5 529.8 499.8 540.1C508.1 550.4 523.3 551.9 533.6 543.6C598.5 490.7 640 410.2 640 320C640 229.8 598.5 149.2 533.6 96.5zM473.1 171C462.8 162.6 447.7 164.2 439.3 174.5C430.9 184.8 432.5 199.9 442.8 208.3C475.3 234.7 496 274.9 496 320C496 365.1 475.3 405.3 442.8 431.8C432.5 440.2 431 455.3 439.3 465.6C447.6 475.9 462.8 477.4 473.1 469.1C516.3 433.9 544 380.2 544 320.1C544 260 516.3 206.3 473.1 171.1zM412.6 245.5C402.3 237.1 387.2 238.7 378.8 249C370.4 259.3 372 274.4 382.3 282.8C393.1 291.6 400 305 400 320C400 335 393.1 348.4 382.3 357.3C372 365.7 370.5 380.8 378.8 391.1C387.1 401.4 402.3 402.9 412.6 394.6C434.1 376.9 448 350.1 448 320C448 289.9 434.1 263.1 412.6 245.5zM80 416L128 416L262.1 535.2C268.5 540.9 276.7 544 285.2 544C304.4 544 320 528.4 320 509.2L320 130.8C320 111.6 304.4 96 285.2 96C276.7 96 268.5 99.1 262.1 104.8L128 224L80 224C53.5 224 32 245.5 32 272L32 368C32 394.5 53.5 416 80 416z"/></svg> 





# currentTarget : 
jispe event listen laga hai wohi select hoga kahi bhi hum select kare 

but
# target : 
jispe click krenge wohi select hoga 

card  >>   img  ,  h1  ,   p 
currenttarget select chose only that file on which event listener is applied 

but target select those which is clicked ... 

























