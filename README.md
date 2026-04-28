# Read Me: Album 13 Generation
Author: Eliana Herzog
NetID: elh58

## **What it Does**
*README.md has What it Does section that describes in one paragraph what your project does*  
The goal of this project is to create a new album of Taylor Swift songs primarily out of pre-existing songs, complete with a new album cover and title. When gievn a datset containing Taylor Swift song lyrics, my project generates a playlist of Taylor Swift songs based on a given song title and then generates a few versions of an original song based on that a title then compares which has the highest similarity score, selecting that one as the playlist to be used. It then generates a cover image for the playlist, using stable diffusion and conditioning before fine-tuning it to attempt to generate an original but realistic looking album cover.
## **Quick Start**
Enter the song titles you want the playlists to be based off of. Then, download the provided dataset file then press run. When the file upload box is running, upload the downloaded dataset file from your device. Once the project is finished running, go to the additional image generation file to finish generating the playlist by creating a cover image.   
*README.md has Quick Start section that concisely explains how to run your project*
##**Evaluation**
README.md has Evaluation section that presents any quantitative results, accuracy metrics, or qualitative outcomes from testing
### Evaluation of prompt designs
The prompts are
1. "Write a song in the style of Taylor Swift for the given title. "
    "Do not include any spoken dialogue or stage directions."
2. "Write a song in the style of Taylor Swift for the given title. "
    "Do not include any spoken dialogue or stage directions."
    "Use emotional and poetic language as if writing a diary entry."
3. "Write a song in the style of Taylor Swift for the given title. "
    "Do not include any spoken dialogue or stage directions."
    "You are a pop artist with a background in country music." 
        a. Temperature of 0.5
        b. Temperature of 2
4. Few-shot learning

| Prompt | Greatest Similarity Score  | Analysis of results  |
|---------------|-------------|--------------------------------|
| 1     | 0.903   |         Dress has a high similarity score despite being very different lyrically from this song. It is a very flirtatious song, while this one is more similar to a song about her love being there in the chaos and wanting a calm love, which is most similar to This Love, gold rush, and sweet nothing, none of which are listed. State of grace should be the most similar, especially due to the lyric "You're my Achilles heel / This is the golden age of something good and right and real"        |
| 2      | 0.822   |         This song is most similar to Lover, New Years Day, or Daylight, all songs about finding your person after a lot of bad relationships. Everything has Changed is correctly rated highly, due to the lines "Your eyes look like comin' home ... all I know is everything has changed" and Holy Ground is also a great choice.   |
| 3a        | ?  |        These are great choices, especially Sweet Nothing and King of my Heart.       |
| 3b     | 0.927      |      While this is pretty differnet from a lot of songs in the database, it is similar to a newwer song Fate of Ophelia which makes this generation interesting in a different way. The creativity of a higher temperature allowed the model to correctly generate something that feels like a song that hadn't been created yet.    |
| 4    | 0.8765         |      3           |

Prompt 3b had the greatest similarity score and prompt 2 had the lowest.

- Compared multiple model architectures or approaches quantitatively with controlled experimental setup

- Performed error analysis with visualization and discussion of failure cases, including analysis of why the model fails and what types of inputs are most challenging
discuss differnet image geneation models
To generate a cover image for the album, I compared multiple model architechtures. First, I used CLIP Embeddings similarity search using a dataset of album images. The results for this were the worst, bearing limited resemblance to the titles chosen. I also was not able to provide detailed guidance for image generation. I then used guided stable diffusion. While the covers weren't great, they looked like they could be real album covers for the title given even if ...
For the image to image, it failed because it looked too similar to the image prompt. It could only really recreate the given 
##**Video Links**
README.md has Video Links section with direct links to your demo and technical walkthrough videos  
Demo:  
Technical Walkthrough: 
## Other Notes
- Used BERT transformer model (section labeled Playlist Generation)
- Used 2 different temperature settings, using temperature as a parameter in calls to Gemini for lyric generation (section labeled Playlist Generation)
- Computed Bert embeddings and conducted sentiment analysis to create a list of songs with lyrics most similar to the given prompt (section labeled Playlist Generation)
- Made multiple calls to Gemini and conducted sentiment analysis on output and used that to generate playlist suggestions (section labeled Playlist Generation)
- Used few-shot examples to generate more realistic song lyrics by providing song lyrics of two very different songs with example of structure of lyric output as well (section labeled Playlist Generation)
- Used 2 different temperature settings, using temperature as a parameter in calls to Gemini for lyric generation (section labeled Playlist Generation)
