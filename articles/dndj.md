# title
dndj

# name
DnDJ

# roles
- front end developer
- ui designer
- visual designer

# languages
- HTML
- CSS

# tools
- Affinity Designer
- Keynote

# article
DnDJ is a web app enabling the easy creation of soundscapes for table-top roleplaying games. I was the primary designer for its logo and UI, and I developed much of the web app's HTML and CSS—most notably, a pure CSS solution for responsive UI elements.

# Design
I started with the logo. I brainstormed imagery that would express our product, sketching several ideas and presenting them to my group. Together we decided on a twenty-sided die wearing headphones, clearly representing both tabletop games and music. The neon orange color, black background, and subtle glow behind the logo creates a club DJ vibe, thematically appropriate for our DnDJ branding. 

Our goal for the product was to make a music tool more powerful than an YouTube playlist, but less complicated than existing soundscape tools. For the UI, I consulted with the two Dungeons and Dragons game masters on our team about their experiences using sound in their games. From this we decided to support three sound types: music, ambience, and sound effects. Using this categorization we created different functionality for each type: music is organized into looping playlists, ambience tracks can be layered, and sound effects only play once. 

I initially made several static mockups of potential layouts. We eventually decided on a "soundboard" UI with large touch targets. I made an interactive prototype for my team using Apple's Keynote software, which my team liked. 

# Development
As I was the visual designer, I took primary responsibiilty for implementing the graphics and animations. Using HTML and SCSS, I recreated the UI from the prototype almost exactly. 

The most memorable thing I worked on was the app's responsiveness. I used media queries and the calc() function to dynamically adjust the soundboard's button size and buttons per row, based on the width of the viewport and the ideal size range of the buttons. This resulted in smooth resizing and button reflow as the window width changes. 

# Redesign
After using the web app for several of our own DnD games, we discovered some aspects of the service that could be improved. Sound effects are rarely used, paging between music and ambience is inconvenient, and Soundcloud's library is more limited than we expected. 

We are considering a new paradigm that gets rid of rarely-used sound effects, packages both music and ambience into "scenes" that eliminate pagination on the soundboard home screen. This redesign greatly simplifies usage of the tool during gameplay, but will also require a new scene builder. We also will redesign the UI to conform to YouTube's API services requirements, so we can legally use YouTube's vast library instead of SoundCloud's more limited one. 