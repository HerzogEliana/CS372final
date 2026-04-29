# Read Me: Playlist Generation
Author: Eliana Herzog  
  NetID: elh58

## **What it Does**
The goal of this project is to create a new album of Taylor Swift songs primarily out of pre-existing songs, complete with a new album cover and title. When gievn a datset containing Taylor Swift song lyrics, my project generates a playlist of Taylor Swift songs based on a given song title and then generates a few versions of an original song based on that a title then compares which has the highest similarity score, selecting that one as the playlist to be used. It then generates a cover image for the playlist, using stable diffusion and conditioning before fine-tuning it to attempt to generate an original but realistic looking album cover.

## **Quick Start**
Enter the song titles you want the playlists to be based off of. Then, download the provided dataset file then press run. When the file upload box is running, upload the downloaded dataset file from your device. Once the project is finished running, go to the additional image generation file to finish generating the playlist by creating a cover image.   

## **Evaluation**
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
| 3a        | .900  |        These are great choices, especially Sweet Nothing and King of my Heart.       |
| 3b     | 0.902      |      While this is pretty differnet from a lot of songs in the database, it is similar to a newwer song Fate of Ophelia which makes this generation interesting in a different way. The creativity of a higher temperature allowed the model to correctly generate something that feels like a song that hadn't been created yet.    |
| 4    | 0.927        |      King of my Heart is a great top similarity because both are about finding love in your darkest moment and being able to ignore what everyone else thought      |

Prompt 4 had the greatest similarity score and prompt 2 had the lowest.

### Comparing multiple model architectures
To generate a cover image for the album, I compared multiple model architechtures. First, I used CLIP Embeddings similarity search using a dataset of album images. The results for this were the worst, bearing limited resemblance to the titles chosen. I also was not able to provide detailed guidance for image generation. I then used guided stable diffusion. While the covers weren't great, they looked like they could be real album covers for the title given even if they did not look like Taylor Swift album covers.
For the image to image, it often failed because it looked too similar to the image prompt. For some images, it only recreated the image with slight differences where as for others there were key details of the original kept that made no sense to keep, such as the shape of the head in the lighthouse playlist cover. 
### Error analysis
The model fails when the prompt given is far from the lyrics. The similarity scores trended higher when I had the model create lyrics for "let's go (battle)", as lyrics about fighting and winning the war and breakups and also hype-up songs are common. However, when I had the model create lyrics for "Hey little songbird" the similarity was much lower because songbirds are not mentioned in very many lyrics. This results in a random seeming assortment of songs.

## **Video Links**
Demo:  https://youtu.be/fn2GZjj7X7A   
Technical Walkthrough: 
