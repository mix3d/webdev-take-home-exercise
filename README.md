# Asana WebDev Take-Home Exercise

## Instructions

Let's pretend that Asana is actually a pet adoption agency. (Our SF office is so dog-friendly that it's not too far a stretch!) We need a web page that contains an image gallery of the pets we have available for adoption. We'd like you to build it.

To help you get started, we've included a few pre-built frontend components, a data file that you should use to populate the gallery, notes on intended user interactions, and guidance about how this gallery supports our efforts to get more pets adopted.

**What to submit:** We'd like to see your incremental work along with finished product, so please either ZIP and submit your version-controlled directory, or link us to your hosted repository.

**What technologies to use:** We'd like you to pick technologies that help us get clear signal on your frontend fundamentals. For that reason, we recommend that you stick with vanilla JS, CSS, and HTML -- but if there's a framework, pre- or post-processor, templating language, or build tooling that you think would make for a stronger submission, go for it.

We'll be grading on five areas:
- **Fidelity -** How well does it work? Does it do what the design calls for?
- **Robustness -** Does the page work across modern web browsers on desktop and mobile?
- **Maintainability -** Is the project written cleanly, organized clearly and documented well?
- **Performance -** Is the page built to load fast and rank well in search engines?
- **Your choice!** Let us know which one (just one!) of these criteria we should use to evaluate your submission:
  - **Design Focus:** How slick and polished are the page's UI and UX?
  - **Growth Focus:** How did the questions from the team trying to boost adoption influence your technical choices?
  - **Tooling Focus:** How did your use of build tools help you ship something high-quality faster?

## Guidance from the design team

"These images should be displayed on the page as a set of thumbnails; clicking on a thumbnail should display a full-sized image to the user."

"Full-size photos should be able to be closed, and the user should be returned to the thumbnail gallery."

## Requirements from the adoption team

"Starting next month, we'll be partnering with a shelter that has 2000 pets available for adoption. We need this page to be able to handle that many listings."

"Most people find out about us from internet searches. We need this page to appear towards the top of search results."

## Madison's notes:

I recognize I did not stick to just fundamentals, I used Vue for the UI layer. Partially for the default setup that includes webpack with HMR for quick development and testing, partially for code corganization, but mostly because I thought I'd be able to accomplish more with my time. I also picked Vue to better handle a higher number of dogs. Assuming the would-be API did not provide pagination built in, I felt I could support a significant portion of dogs, plus reactively searching / filtering on a larger set of data that the site would likely require for users to manage sorting through that many dogs.

Ultimately, however, I would like to be judged on the Design.

I definitely went far beyond the initial task, filling in details I assumed a would help a would-be dog adoption facility, but also in line with all the other dog adoption websites I looked at for research. Showing more doggo information, even if randomized, makes them more personable, and being able to select favorites helps sort through a large set of data. The would-be final feature would be a dropdown list of the saved dogs, which would also give you the fullscreen image.

--

List of dog names from https://www.akc.org/expert-advice/lifestyle/unique-dog-names/, the images alone did not seem to evoke enough "adopt me"-ness, and I wanted to add some additional info to intrigue would-be adopters more.

Background image from https://img.freepik.com/free-vector/bons-and-foot-prints-pattern-background_1374-18.jpg?size=338&ext=jpg but edited in PS for actual seamless tiling.

https://fonts.google.com/specimen/Gorditas?selection.family=Gorditas|Open+Sans

The Gortitas font is named almost exactly like Asana's font, seemed fun, and even mentioned dogs in the description. Sold!

# doggo

> A Vue.js approach to Asana's takehome project

## Build Setup

``` bash
# install dependencies
npm install

# serve with hot reload at localhost:8080
npm run dev

# build for production with minification
npm run build
```

![Screenshot](static/showcase.jpg)