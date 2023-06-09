# Testing

Return back to the [README.md](README.md) file.

## Code Validation

### HTML

I have used the recommended [HTML W3C Validator](https://validator.w3.org) to validate all of my HTML files.

| Page | W3C URL | Screenshot | Notes |
| --- | --- | --- | --- |
| Home | [W3C](https://validator.w3.org/nu/?doc=https%3A%2F%2Fjamesh003.github.io%2FRocket-Launch%2F) | ![screenshot](documentation/testing/html-validation-index.png) | Pass: No Errors |
| Quiz | [W3C](https://validator.w3.org/nu/?doc=https%3A%2F%2Fjamesh003.github.io%2FRocket-Launch%2Fquiz.html) | ![screenshot](documentation/testing/html-validation-quiz.png) | Pass: No Errors |

### CSS

I have used the recommended [CSS Jigsaw Validator](https://jigsaw.w3.org/css-validator) to validate all of my CSS files.

| File | Jigsaw URL | Screenshot | Notes |
| --- | --- | --- | --- |
| style.css | [Jigsaw](https://jigsaw.w3.org/css-validator/validator?uri=https%3A%2F%2Fjamesh003.github.io%2FRocket-Launch%2Fquiz.html&profile=css3svg&usermedium=all&warning=1&vextwarning=&lang=en) | ![screenshot](documentation/testing/css-validation-home.png) | Pass: No Errors |


### JavaScript

I have used the recommended [JShint Validator](https://jshint.com) to validate all of my JS files.

| File | Screenshot | Notes |
| --- | --- | --- |
| script.js | ![screenshot](documentation/testing/js-validation-script.png) | One undefined variable |
| questions.js | ![screenshot](documentation/testing/js-validation-questions.png) | One unused variable |

## Browser Compatibility

I've tested my deployed project on multiple browsers to check for compatibility issues.

| Browser | Screenshot | Notes |
| --- | --- | --- |
| Chrome | ![screenshot](documentation/testing/chrome-testing.png) | Works as expected |
| Firefox | ![screenshot](documentation/testing/firefox-testing.png) | Works as expected |
| Edge | ![screenshot](documentation/testing/edge-testing.png) | Works as expected |
| Safari | ![screenshot](documentation/testing/safari-testing-explosion-error.png) | Works as expected |
| Brave | ![screenshot](documentation/testing/brave-testing.png) | Works as expected |
| Opera | ![screenshot](documentation/testing/opera-testing.png) | Works as expected |

## Responsiveness

I've tested my deployed project on multiple devices to check for responsiveness issues.

| Device | Screenshot | Notes |
| --- | --- | --- |
| Mobile (DevTools) | ![screenshot](documentation/testing/mobile-devtools-responsiveness.png) | Works as expected |
| Tablet (DevTools) | ![screenshot](documentation/testing/tablet-devtools-responsiveness.png) | Works as expected |
| Desktop | ![screenshot](documentation/testing/desktop-responsiveness.png) | Works as expected |
| iPhone 11 | ![screenshot](documentation/testing/iphone11-responsiveness1.PNG) | Works as expected |
| iPhone 11 | ![screenshot](documentation/testing/iphone11-responsiveness2.PNG) | Works as expected |

## Lighthouse Audit

I've tested my deployed project using the Lighthouse Audit tool to check for any major issues.

| Page | Size | Screenshot | Notes |
| --- | --- | --- | --- |
| Home | Mobile | ![screenshot](documentation/testing/mobile-home-lighthouse.png) | No warnings |
| Home | Desktop | ![screenshot](documentation/testing/desktop-home-lighthouse.png) | No warnings |
| Quiz | Mobile | ![screenshot](documentation/testing/mobile-quiz-lighthouse.png) | Some minor warnings |
| Quiz | Desktop | ![screenshot](documentation/testing/desktop-quiz-lighthouse.png) | No warnings |

## User Story Testing

| User Story | Screenshot |
| --- | --- |
| As a new site user, I would like to understand the purpose of the site, so that I can decide if I want to use it. | ![screenshot](documentation/user-stories/user-stories-purpose.png) |
| As a new site user, I would like to understand the aim of the game, so that I can maximise my chances | ![screenshot](documentation/user-stories/user-stories-aim.png) |
| As a new site user, I would like to see strong enticing visuals, so that I can enjoy the experience. | ![screenshot](documentation/user-stories/user-stories-purpose.png) |
| As a new site user, I would like to readily understand the layout of the game/quiz, so that I don't waste time figuring it out.| ![screenshot](documentation/user-stories/user-stories-undestand.png) |
As a new site user, I would like to be able to control any sound, so that I can tailor my experience to my needs.| ![screenshot](documentation/user-stories/user-stories-volume.png) |
As a new site user, I would like there to be an element of jeopardy to the game, to increase my gaming experience.| ![screenshot](documentation/user-stories/user-stories-jeopardy.png) |
| As a returning site user, I would like to have a random selection of quesions, so that I can attempt the game multiple times. | ![screenshot](documentation/user-stories/user-stories-random.png) |

## Bugs

- FontAwesome icons displaying as boxes

    ![screenshot](documentation/testing/font-awesome-icons-bug.png)

    - To fix this, I removed the font-family from `*::before, ::after` 
    and instead added it to:

    ```css
    * {
        font-family: Space Mono, Lato;
    }
    ```

- Audio sound effects would play every time page reloaded

    ![screenshot](documentation/testing/audio-bug.png)

    - To fix this, I added `muted` to each audio html tag.

- Timer starting as soon as page loaded.

    ![screenshot](documentation/testing/timer-bug.png)

    - To fix this, I moved this line `timerId = setInterval(countdown, 1000);` inside of the startQuiz function.

- Background image not changing between day and night scene in relation to timeOfDay function

    ![screenshot](documentation/testing/timeofday-bug.png)

    - To fix this, I changed the code to this `bgImg.style.backgroundImage = "url('assets/images/bg-day.jpg')";`. By adding `url()` it fixed the code.

- Rocket kept exploding when the timer would reach zero regardless of quantity of correct answers.

    ![screenshot](documentation/testing/constant-destruct-bug.png)

    - To fix this, I changed the code to this to target lack of correct scores instead of number of incorrect scores

    ```js
    function countdown() {
    if (countdownTimer < 0 && correctScore < 5) {
        hideElements();
        initiateSelfDestruct();
    } else {
        timer.innerHTML = countdownTimer + ':00';
        countdownTimer--;
    }}
    ```

    - No sound effects playing on Safari on either mobile or desktop

    ![screenshot](documentation/testing/safari-testing-explosion-error.png)

    - To fix this, I added these lines of code to the playAudio function to load the audio and play from the beginning.

    ```js
        audio.load();
        audio.pause();
        audio.currentTime = 0;
    ```

- Positioning error of rocket & height of image too long for viewport on iPhone 11.

    ![screenshot](documentation/testing/iphone11-responsiveness-position-error.PNG)

    - To fix this, I changed the code the min-height of the body to 100svh.
    ```css
    min-height: 100svh;
    ```

## Unfixed Bugs

 - Mis-alignment of the rocket and twinkle effect when launched on iPhone 11.

    ![screenshot](documentation/testing/iphone-rocket-position-error.PNG)
    ![screenshot](documentation/testing/iphone-twinkle-position-error.PNG)

    - I attempted to fix this by using a CSS prefix, but this did not rectify the issue.
    ```css
    @-webkit-keyframes rocket-launch {
    0%  {-webkit-transform: rotate(0deg);transform: rotate(0deg);}
    100% {-webkit-transform: rotate(30deg) scale(0.0001);transform: rotate(30deg) scale(0.0001); bottom: 42.4em; left: 16em;}
    }
    ```

    - I also tried to change the code to reference the position from the `top` instead of `bottom`, however this distorted the launch sequence.
    ```css
    @keyframes rocket-launch {
    0%  {-webkit-transform: rotate(0deg);transform: rotate(0deg);}
    100% {-webkit-transform: rotate(30deg) scale(0.0001);transform: rotate(30deg) scale(0.0001); top: 1em; left: 16em;}
    }
    ```


There are no remaining bugs that I am aware of.
