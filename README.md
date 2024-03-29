## Introduction

The Melon Playlist Dataset is a public MIR dataset provided by Kakao Corp. Using the data from [Melon](http://www.melon.com), the most popular music streaming platform in Korea, and used in research by Music Technology Group. On this page, we give a summary of the dataset and describe how to access it. Check the official web page for more details.


The dataset was originally created for the task of automatic playlist continuation, and it was used for a competition between April and July 2020. The platform [Kakao Area](https://arena.kakao.com/c/8) was used to host the competition. After the end of the competition, this platform offers the chance to submit solutions that can be used for benchmarking since the test dataset is private.

The Melon Playlist Dataset contains 148,826 playlists in the training set and 649,091 songs, it also contains genre information for the songs and tag information for the playlists.  For all the songs, the mel-spectrogram representation of the audio is provided which enables the possibility of applying content-based approaches.

### Download

In order to access the dataset is required to register and login in [Kakao Arena](https://arena.kakao.com/c/8/data), after that the link to download each file of the dataset will be available.

Update 2024-02-12: Kakao Arena is currently unavailable. Contact us for further details to access the dataset.

### Description of the files 

 - `song_meta.json`: contains information for the 649,091 songs, including:
   - `_id`: Song ID
   - `album_id`: Album ID
   - `artist_id_basket`: Artist ID list
   - `artist_name_basket`: artist list
   - `song_name`: song title
   - `song_gn_gnr_basket`: song genre list
   - `song_gn_dtl_gnr_basket`: Song sub-genre list
   - `issue_date`: release date

  - `genre_gn_all.json`: Contains information of the genres which are present in the fileds `song_gn_gnr_basket` and `song_gn_dtl_gnr_basket` of the above `song_meta.json`.
  - `train.json`: Contains training information for 115,071 playlists, including: 
    - `id`: Playlist ID
    - `plylst_title`: playlist title
    - `tags`: list of tags
    - `songs`: song list
    - `like_cnt`: number of likes
    - `updt_date`: date of modification
  - `val.json`: Contains playlists that are used in the competition to compute the results in the leaderboard. Contains partial information for  23,015 playlists.
  - `test.json`: Contains playlists that are used in the competition to compute the final leadearboard. It contains information for 10,740 playlists.
  - `arena_mel_{0~39}.tar`: These files contains the mel-spectrogram data for the song. One npy file is assigned for each song ID that appears in the files above. You can load it with numpy like this:

```
import numpy as np

mel = np.load("0.npy")
```

Song IDs are assigned from 0 to 707988. Since the number of files is large, each npy file is located in a folder which is named in the following way: {floor(ID / 1000)}. For example, in the case of a file with a an ID of 415263 the loaction is 415/415263.npy


### Cite 

Please citing the following publication when using the dataset: 

> Ferraro A., Kim Y., Lee S., Kim. B., Jo N., Lim S., Lim S., Jan J., Kim S., Serra X. & Bogdanov D. (2021).  "Melon Playlist Dataset: a public dataset for audio-based playlist generation and music tagging". International Conference on Acoustics, Speech and Signal Processing (ICASSP 2021).

```
@conference {ferraro2021melon,
    author = "Ferraro, Andres and Kim, Yuntae and Lee, Soohyeon and Kim, Biho and Jo, Namjun and Lim, Semi and Lim, Suyon and Jang, Jungtaek and Kim, Sehwan and Serra, Xavier and Bogdanov, Dmitry",
    title = "Melon Playlist Dataset: a public dataset for audio-based playlist generation and music tagging",
    booktitle = "International Conference on Acoustics, Speech and Signal Processing (ICASSP 2021)",
    year = "2021",
}
```
