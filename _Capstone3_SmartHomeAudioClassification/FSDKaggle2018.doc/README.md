
# Freesound Dataset Kaggle 2018 (FSDKaggle2018)



## Citation

If you use the FSDKaggle2018 dataset or part of it, please cite our <a href="https://arxiv.org/abs/1807.09902" target="_blank">DCASE 2018 paper</a>:

>Eduardo Fonseca, Manoj Plakal, Frederic Font, Daniel P. W. Ellis, Xavier Favory, Jordi Pons, Xavier Serra. "General-purpose Tagging of Freesound Audio with AudioSet Labels: Task Description, Dataset, and Baseline". *Proceedings of the DCASE 2018 Workshop* (2018)

You can also consider citing our <a href="https://repositori.upf.edu/bitstream/handle/10230/33299/fonseca_ismir17_freesound.pdf?sequence=1&isAllowed=y" target="_blank">ISMIR 2017 paper</a>, which describes how we gathered the manual annotations included in FSDKaggle2018.

>Eduardo Fonseca, Jordi Pons, Xavier Favory, Frederic Font, Dmitry Bogdanov, Andres Ferraro, Sergio Oramas, Alastair Porter, and Xavier Serra, "Freesound Datasets: A Platform for the Creation of Open Audio Datasets", In *Proceedings of the 18th International Society for Music Information Retrieval Conference*, Suzhou, China, 2017

### Contact

You are welcome to contact Eduardo Fonseca should you have any questions at eduardo.fonseca@upf.edu.

## About this dataset

Freesound Dataset Kaggle 2018 (or **FSDKaggle2018** for short) is an audio dataset containing 11,073 audio files annotated with 41 labels of the <a href="https://research.google.com/audioset////////ontology/index.html" target="_blank">AudioSet Ontology</a> [1]. FSDKaggle2018 has been used for the Task 2 of the *Detection and Classification of Acoustic Scenes and Events* (DCASE) Challenge 2018. Please visit the <a href="http://dcase.community/challenge2018/task-general-purpose-audio-tagging" target="_blank">DCASE2018 Challenge Task 2 website</a> for more information. This Task was hosted on the Kaggle platform as a competition titled <a href="https://www.kaggle.com/c/freesound-audio-tagging" target="_blank">Freesound General-Purpose Audio Tagging Challenge</a>. It was organized by researchers from the Music Technology Group of Universitat Pompeu Fabra, and from Google Research’s Machine Perception Team.

The goal of this competition was to build an audio tagging system that can categorize an audio clip as belonging to one of a set of 41 diverse categories drawn from the AudioSet Ontology.

All audio samples in this dataset are gathered from <a href="https://freesound.org" target="_blank">Freesound</a> [2] and are provided here as uncompressed PCM 16 bit, 44.1 kHz, mono audio files. Note that because Freesound content is collaboratively contributed, recording quality and techniques can vary widely. 

The ground truth data provided in this dataset has been obtained after a data labeling process which is [described below](#Data-labeling-process) in the *Data labeling process* section. FSDKaggle2018 clips are unequally distributed in the following **41 categories** of the AudioSet Ontology: 

`"Acoustic_guitar"`, `"Applause"`, `"Bark"`, `"Bass_drum"`, `"Burping_or_eructation"`, `"Bus"`, `"Cello"`, `"Chime"`, `"Clarinet"`, `"Computer_keyboard"`, `"Cough"`, `"Cowbell"`, `"Double_bass"`, `"Drawer_open_or_close"`, `"Electric_piano"`, `"Fart"`, `"Finger_snapping"`, `"Fireworks"`, `"Flute"`, `"Glockenspiel"`, `"Gong"`, `"Gunshot_or_gunfire"`, `"Harmonica"`, `"Hi-hat"`, `"Keys_jangling"`, `"Knock"`, `"Laughter"`, `"Meow"`, `"Microwave_oven"`, `"Oboe"`, `"Saxophone"`, `"Scissors"`, `"Shatter"`, `"Snare_drum"`, `"Squeak"`, `"Tambourine"`, `"Tearing"`, `"Telephone"`, `"Trumpet"`, `"Violin_or_fiddle"`, `"Writing"` 

Here are some other relevant characteristics of FSDKaggle2018:

* The dataset is split into a train set and a test set.

* The **train set** is meant to be for system development and includes **~9.5k samples unequally distributed among 41 categories**. The minimum number of audio samples per category in the train set is 94, and the maximum 300. The duration of the audio samples ranges from 300ms to 30s due to the diversity of the sound categories and the preferences of Freesound users when recording sounds. The total duration of the train set is roughly 18h.

* Out of the ~9.5k samples from the train set, **~3.7k have manually-verified ground truth annotations** and **~5.8k have non-verified annotations**. The non-verified annotations of the train set have a quality estimate of **at least** 65-70% in each category. Checkout the *Data labeling process* section below for more information about this aspect.

* Non-verified annotations in the train set are properly flagged in `train.csv` so that participants can opt to use this information during the development of their systems.

* The **test set** is composed of **1.6k samples with manually-verified annotations** and with a similar category distribution than that of the train set. The total duration of the test set is roughly 2h.

* All audio samples in this dataset have a **single label** (i.e. are only annotated with one label). Checkout the *Data labeling process* section below for more information about this aspect. A single label should be predicted for each file in the test set.



## Data labeling process

The data labeling process started from a manual mapping between Freesound tags and AudioSet Ontology categories (or *labels*), which was carried out by researchers at the Music Technology Group, Universitat Pompeu Fabra, Barcelona. Using this mapping, a number of Freesound audio samples were **automatically annotated** with labels from the AudioSet Ontology. These annotations can be understood as weak labels since they express the presence of a sound category in an audio sample.  

Then, a **data validation process** was carried out in which a number of participants did listen to the annotated sounds and manually assessed the presence/absence of an automatically assigned sound category, according to the AudioSet category description.

Audio samples in FSDKaggle2018 are only annotated with a single ground truth label (see `train.csv`). A total of **3,710 annotations** included in the train set of FSDKaggle2018 are annotations that have been **manually validated** as present and predominant (some with inter-annotator agreement but not all of them). This means that in most cases there is no additional acoustic material other than the labeled category. In few cases there may be some additional sound events, but these additional events won't belong to any of the 41 categories of FSDKaggle2018.

The rest of the annotations have **not** been manually validated and therefore some of them could be inaccurate. Nonetheless, we have **estimated** that **at least** 65-70% of the non-verified annotations per category **in the train set** are indeed correct. It can happen that some of these non-verified audio samples present several sound sources even though only one label is provided as ground truth. These additional sources are typically out of the set of the 41 categories, but in a few cases they could be within.

More details about the data labeling process can be found in [3].


## License

FSDKaggle2018 has licenses at two different levels, as explained next.

All sounds in Freesound are released under Creative Commons (CC) licenses, and each audio clip has its own license as defined by the audio clip uploader in Freesound. For attribution purposes and to facilitate attribution of these files to third parties, we include a relation of the audio clips included in FSDKaggle2018 and their corresponding license. The licenses are specified in the files `train_post_competition.csv` and `test_post_competition_scoring_clips.csv`.

In addition, FSDKaggle2018 as a whole is the result of a curation process and it has an additional license. FSDKaggle2018 is released under <a href="https://creativecommons.org/licenses/by/4.0/" target="_blank">CC-BY</a>. This license is specified in the `LICENSE-DATASET` file downloaded with the `FSDKaggle2018.doc` zip file.


## Files

FSDKaggle2018 can be downloaded as a series of zip files with the following directory structure:

<div class="highlight"><pre><span></span>root
│  
└───FSDKaggle2018.audio_train/                       Audio clips in the train set
│   
└───FSDKaggle2018.audio_test/                        Audio clips in the test set
│   
└───FSDKaggle2018.meta/                              Files for evaluation setup
│   │            
│   └───train_post_competition.csv                   Data split and ground truth for the train set
│   │            
│   └───test_post_competition_scoring_clips.csv      Ground truth for the test set         
│   
└───FSDKaggle2018.doc/
    │            
    └───README.md                                    The dataset description file that you are reading
    │            
    └───LICENSE-DATASET                              License of the FSDKaggle2018 dataset as an entity   
</pre></div>

**NOTE**: the original `train.csv` file provided during the competition has been updated with more metadata (licenses, Freesound ids, etc.) into `train_post_competition.csv`. Likewise, the original `test.csv` that was not public during the competition is now available with ground truth and metadata as `test_post_competition_scoring_clips.csv`. The file name `test_post_competition_scoring_clips.csv` refers to the fact that only the 1600 clips used for systems' ranking are included. During the competition, an additional subset of *padding* clips was added in order to prevent undesired practices. This *padding* subset (that was never used for systems' ranking) is no longer included in the dataset (see our DCASE 2018 paper for more details.)

Each row (i.e. audio clip) of the `train_post_competition.csv` file contains the following information:

- `fname`: the file name
- `label`: the audio classification label (ground truth)
- `manually_verified`: Boolean (1 or 0) flag to indicate whether or not that annotation has been manually verified; see description above for more info
- `freesound_id`: the Freesound id for the audio clip
- `license`: the license for the audio clip

Each row (i.e. audio clip) of the `test_post_competition_scoring_clips.csv` file contains the following information:

- `fname`: the file name
- `label`: the audio classification label (ground truth)
- `usage`: string that indicates to which Kaggle leaderboard the clip was associated during the competition: `Public` or `Private`
- `freesound_id`: the Freesound id for the audio clip
- `license`: the license for the audio clip

## Baseline System

A CNN baseline system for FSDKaggle2018 is available at <a href="https://github.com/DCASE-REPO/dcase2018_baseline/tree/master/task2" target="_blank">https://github.com/DCASE-REPO/dcase2018_baseline/tree/master/task2</a>.


## References and links

[1] Jort F Gemmeke, Daniel PW Ellis, Dylan Freedman, Aren Jansen, Wade Lawrence, R Channing Moore, Manoj Plakal, and Marvin Ritter. "Audio set: An ontology and human-labeled dartaset for audio events." Proceedings of the Acoustics, Speech and Signal Processing International Conference, 2017.

[2] Frederic Font, Gerard Roma, and Xavier Serra. "Freesound technical demo." Proceedings of the 21st ACM international conference on Multimedia, 2013. [https://freesound.org](https://freesound.org)

[3] Eduardo Fonseca, Jordi Pons, Xavier Favory, Frederic Font, Dmitry Bogdanov, Andres Ferraro, Sergio Oramas, Alastair Porter, and Xavier Serra. "Freesound Datasets: A Platform for the Creation of Open Audio Datasets." Proceedings of the International Conference on Music Information Retrieval, 2017. [PDF here](https://ismir2017.smcnus.org/wp-content/uploads/2017/10/161_Paper.pdf)


Freesound Datasets platform: <a href="https://datasets.freesound.org/" target="_blank">https://datasets.freesound.org/</a>  
Freesound: <a href="https://freesound.org" target="_blank">https://freesound.org</a>  
Eduardo Fonseca's personal website: <a href="http://www.eduardofonseca.net/" target="_blank">http://www.eduardofonseca.net/</a>  
More datasets collected by us: <a href="http://www.eduardofonseca.net/datasets/" target="_blank">http://www.eduardofonseca.net/datasets/</a>

## Acknowledgments

This work is partially supported by the European Union’s Horizon 2020 research and innovation programme under grant agreement No 688382 <a href="https://www.audiocommons.org/" target="_blank">AudioCommons</a>. Eduardo Fonseca is also sponsored by a <a href="https://ai.googleblog.com/2018/03/google-faculty-research-awards-2017.html" target="_blank">Google Faculty Research Award 2017</a>. We thank everyone who contributed to FSDKaggle2018 with annotations.
