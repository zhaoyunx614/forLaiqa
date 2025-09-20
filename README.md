Letter Website for Laiqa - Complete Setup Guide
Project Structure

Create this exact folder structure:

your-github-repository/
│
├── index.html          (main website file)
├── README.md          (this file)
│
├── images/            (folder for all images)
│   ├── image1.jpg
│   ├── image2.jpg
│   └── image3.jpg
│
├── pdfs/              (folder for all PDF letters)
│   ├── letter1.pdf
│   ├── letter2.pdf
│   └── letter3.pdf
│
└── songs/             (folder for all music files)
    ├── song1.mp3
    ├── song2.mp3
    ├── song3.mp3
    ├── song4.mp3
    └── song5.mp3

Step-by-Step Setup Instructions
Step 1: Create GitHub Repository

    Go to github.com and sign in
    Click the green "New" button
    Name your repository (e.g., "letters-for-laiqa")
    Set it to PRIVATE (important for privacy)
    Don't initialize with README (we're creating our own)
    Click "Create repository"

Step 2: Set Up Local Project in VS Code

    Open VS Code
    Create a new folder on your computer for the project
    Open that folder in VS Code (File > Open Folder)
    Create the folder structure shown above:
        Right-click in VS Code sidebar > New Folder > name it "images"
        Right-click in VS Code sidebar > New Folder > name it "pdfs"
        Right-click in VS Code sidebar > New Folder > name it "songs"

Step 3: Add Website Files

    Create index.html: Right-click > New File > "index.html"
    Copy the entire HTML code from the artifact above into index.html
    Save the file (Ctrl+S or Cmd+S)
    Create README.md: Right-click > New File > "README.md"
    Copy this README content into it

Step 4: Add Your Content Files

    Images: Copy your image files into the "images" folder
        Supported formats: .jpg, .jpeg, .png, .gif
        Name them clearly: photo1.jpg, memory1.png, etc.
    PDFs: Copy your PDF letters into the "pdfs" folder
        Name them: letter1.pdf, letter2.pdf, etc.
    Songs: Copy your MP3 files into the "songs" folder
        Supported format: .mp3
        Name them: song1.mp3, favorite-song.mp3, etc.

Step 5: Customize Content in index.html

Find the letterContents object in the JavaScript section (around line 650) and modify each letter:
javascript

1: {
    title: "Your Letter Title Here",
    type: "text",  // Choose: "text", "images", "pdf", or "mixed"
    text: "Your actual letter text goes here...",
    songs: ["your-song.mp3"]  // List your song files
}

Step 6: Upload to GitHub

    In VS Code, open Terminal (View > Terminal)
    Run these commands one by one:

bash

git init
git add .
git commit -m "Initial website upload"
git branch -M main
git remote add origin https://github.com/YOUR-USERNAME/YOUR-REPO-NAME.git
git push -u origin main

Step 7: Enable GitHub Pages

    Go to your repository on GitHub
    Click "Settings" tab
    Scroll down to "Pages" section in left sidebar
    Under "Source", select "Deploy from a branch"
    Choose "main" branch and "/ (root)" folder
    Click Save
    Wait 2-3 minutes for deployment
    Your site will be at: https://YOUR-USERNAME.github.io/YOUR-REPO-NAME/

Customization Guide
Changing Envelope Content (Line ~650-750 in index.html)

Each envelope is configured in the letterContents object. Here's what each property does:
javascript

letterContents = {
    1: {  // Envelope number (1-20)
        title: "Letter Title",  // Title shown at top of letter page
        type: "text",  // Content type - determines layout
        text: "Letter content",  // Text content (optional)
        images: ["img1.jpg", "img2.jpg"],  // Image files (optional)
        pdf: "letter.pdf",  // PDF file (optional)
        songs: ["song1.mp3", "song2.mp3"]  // Music files (optional)
    }
}

Content Types Explained:

    "text" - Only displays text content

javascript

   type: "text",
   text: "Your letter text here..."

    "images" - Displays image gallery with optional text

javascript

   type: "images",
   images: ["photo1.jpg", "photo2.jpg"],
   text: "Caption or description"

    "pdf" - Embeds a PDF document

javascript

   type: "pdf",
   pdf: "letter-scan.pdf"

    "mixed" - Combines text and images

javascript

   type: "mixed",
   text: "Letter text...",
   images: ["memory1.jpg", "memory2.jpg"]

Styling Modifications
Change Background Color (Line ~30)
css

body {
    background-color: #B6AD90;  /* Change this hex code */
}

Change Title Font (Line ~55)
css

.main-title {
    font-family: 'Times New Roman', serif;  /* Change font here */
    font-size: 4rem;  /* Change size */
    color: #3a3428;  /* Change color */
}

Change Envelope Appearance (Line ~120)
css

.envelope {
    width: 100px;  /* Envelope width */
    height: 70px;  /* Envelope height */
    background: linear-gradient(135deg, #f4e8d0 0%, #e8dcc0 100%);  /* Colors */
}

Change Letter Page Background (Line ~220)
css

.letter-content {
    background: linear-gradient(to bottom, #f7f3e9, #f0e8d8);  /* Parchment colors */
}

Adding More Envelopes

The website is set for 20 envelopes. To add more:

    Change the loop limit in generateEnvelopes() function (Line ~700):

javascript

for (let i = 1; i <= 25; i++) {  // Change 20 to your number

    Change the loop limit in generateLetterPages() function (Line ~720):

javascript

for (let i = 1; i <= 25; i++) {  // Same number as above

    Add more letter configurations in letterContents object:

javascript

21: { title: "Letter 21", type: "text", text: "Content", songs: [] },
22: { title: "Letter 22", type: "text", text: "Content", songs: [] },
// etc...

Music Player Customization
Change Play Button Style (Line ~340)
css

.play-btn {
    width: 40px;  /* Button size */
    height: 40px;
    background: linear-gradient(135deg, #6b5d4f, #4a4032);  /* Button colors */
}

Change Song Title Display (Line ~380)
css

.song-title {
    font-size: 1rem;  /* Text size */
    color: #3a3428;  /* Text color */
}

File Requirements
Images

    Format: JPG, PNG, GIF
    Recommended size: Under 2MB per image
    Optimal dimensions: 800x600 pixels or smaller

PDFs

    Format: Standard PDF
    Size: Under 5MB recommended
    Make sure PDFs are web-optimized

Songs

    Format: MP3
    Size: Under 10MB per song recommended
    Bitrate: 128-192 kbps for web optimization

Troubleshooting
Envelopes Not Clickable

    Check browser console for JavaScript errors (F12 > Console)
    Verify all quotation marks in letterContents are straight quotes, not curly

Images Not Showing

    Check file names match exactly (case-sensitive)
    Ensure images are in the "images" folder
    Verify image file extensions (.jpg not .JPG)

PDFs Not Loading

    Check file name matches exactly
    Ensure PDF is in "pdfs" folder
    Try opening PDF directly to verify it's not corrupted

Music Not Playing

    Verify MP3 files are in "songs" folder
    Check file names match exactly
    Ensure MP3 files aren't corrupted
    Some browsers block autoplay - user must click play button

Website Not Loading on GitHub Pages

    Wait 5-10 minutes after pushing changes
    Check Settings > Pages to ensure it's enabled
    Verify index.html is in root folder (not in subfolder)
    Check repository is public or you're logged in to view private repo

Advanced Customizations
Adding Fade-In Animation for Letters (Add to CSS)
css

@keyframes letterFadeIn {
    0% { opacity: 0; transform: translateY(20px); }
    100% { opacity: 1; transform: translateY(0); }
}

.letter-content {
    animation: letterFadeIn 0.8s ease;
}

Adding Background Pattern (Add to CSS)
css

body::before {
    content: '';
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-image: url('images/pattern.png');
    opacity: 0.1;
    pointer-events: none;
}

Making Envelopes Shake on Hover (Replace hover effect)
css

@keyframes shake {
    0%, 100% { transform: rotate(0deg); }
    25% { transform: rotate(-2deg); }
    75% { transform: rotate(2deg); }
}

.envelope:hover {
    animation: shake 0.3s ease;
}

Adding Letter Dates

In letterContents object:
javascript

1: {
    title: "Letter 1",
    date: "January 1, 2024",  // Add date
    type: "text",
    text: "Content..."
}

Then display it by modifying the letter page generation code.
Security & Privacy

Since this is private:

    Keep repository PRIVATE in GitHub settings
    Only share link with intended recipient
    Can add password protection using GitHub Pages access control (requires GitHub Pro)
    Consider removing sensitive content before making public

Quick Reference - Line Numbers

    Global Styles: Lines 10-30
    Title Styling: Lines 50-70
    Sparkle Animation: Lines 75-95
    Envelope Styles: Lines 100-180
    Letter Page Styles: Lines 200-280
    Music Player Styles: Lines 330-400
    Responsive Design: Lines 450-600
    Letter Contents Configuration: Lines 650-750
    Envelope Generation Function: Lines 690-710
    Letter Page Generation: Lines 720-900
    Animation Controls: Lines 950-1000
    Music Controls: Lines 1010-1050

Need Help?

If something isn't working:

    Check browser console for errors (F12)
    Verify all file names match exactly
    Ensure folder structure is correct
    Test locally first before pushing to GitHub
    Clear browser cache if changes don't appear

Remember to save all files after making changes and commit+push to GitHub to update the live site.