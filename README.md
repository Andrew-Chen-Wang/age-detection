# Age Detection
Published by: Andrew Chen Wang

Started on 9 June 2020

This project aims to use computer vision alongside text-to-speech _or_ speech recognition
to identify age during the following scenarios:

1. Static images
  - This will only work with computer vision.
  - [Conclusion of paper 13 June 2020](https://github.com/Andrew-Chen-Wang/static-image-age-detection):
    age detector is terrible, even with the 
    multi-image processing. It is most likely due to the model, as most of my input
    data is of teenagers and they're not particularly well-documented in the
    age detector model. Moving on to integrating with audio recordings to really
    make this work much better! That's of my opinion at least.
    
2. Chatrooms and Audio Recordings
  - This would only work with the text-to-speech or speech recognition, depending
  on the context of the input.
  - With audio recordings, you can more easily identify age based on pitch and
  other factors than simple text-to-speech.
  - Text-to-speech recognition should NOT formulate words. Instead, it should
  formulate syllables (like Siri and Alexa) and piece those together based on
  the amount of spaces between each "word." This is part of growing up: you
  can't pronounce your TH's correctly.
3. (Live) Videos
  - Live videos utilizes both computer vision and speech recognition.
  - In videos, multiple people could be talking, so it is important to
  figure out **who** is talking and try our best to correctly identify the age
  of a person based on the inputs.

The goal is the third point. Each goal will be marked as a milestone as two set-pieces
in tackling videos. Age detection today is very good; however, [many lack the integration
of speech recognition and face in combination.
<sup>[1]</sup>](https://www.psychologicabelgica.com/articles/10.5334/pb.aq/)
Although the paper was published in 2014 and I believe my Googling skills to be top-notch,
I still don't think anyone has done this.

The main problem is the integration of each component. Obviously, the computer vision
weighs more than the speech recognition (especially if it's text-to-speech), but
finding a balance between these two components is what I'm looking for.

---
### Pre-Log of Initial Thoughts

Dated: 13 June 2020

My thoughts before I found this paper was to combine the inputs at some random
layer of the network. (Oh FYI, I've never learned how to do ML, so lots of this is
trial and error commits with practically zero unittests). I was hoping to give more
weight or bias to the one that had more confidence, and this could be for multiple
reasons such as a lack of images and only voice chat, a lack of sound and only
video stream, etc. in addition to just confidence of detection and running through
the layers itself.

In addition to those inputs, throughout the layer, we'll be able to figure out
other human attributes such as age and ethnicity, which could assist the speech
recognition. Especially when it comes to 

After reading this paper, I can safely say that there are several factors
that should outweigh others. A notable point was male detection vs.
female detection can lend to differences in estimation. In the paper,
it is said that female voices lead to better estimation, whereas
male faces lead to better estimation.

I will take into account all these factors.

---
### License

Copyright 2020 Andrew Chen Wang

   Licensed under the Apache License, Version 2.0 (the "License");
   you may not use this file except in compliance with the License.
   You may obtain a copy of the License at

       http://www.apache.org/licenses/LICENSE-2.0

   Unless required by applicable law or agreed to in writing, software
   distributed under the License is distributed on an "AS IS" BASIS,
   WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
   See the License for the specific language governing permissions and
   limitations under the License.

---
### Credit + References

1. Moyse, E., 2014. Age Estimation from Faces and Voices: A Review. Psychologica Belgica, 54(3), pp.255–265. DOI: http://doi.org/10.5334/pb.aq
