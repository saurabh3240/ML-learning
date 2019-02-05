Context 

**System having understanding of Environment**

before  processing the audio text file our system have some meta information associated with the audio file such as :

- type of document

- physician or nurse
  - slow talker 
  - fast talker
  - heavily accented
- length of audio
- quality of audio
- expected TAT for the audio 
- Priority of the audio

- service line or speciality of the case
- hospital specific information 
- patient meta information such as gender and age.

So our system have proper understanding of such meta information that is useful in various stage associated with transcription process such as 

- information related to audio , speaker , document template can be used by ASR engine to transcribe it  better  
- this meta information can be used by ML improvement phase (12 ) and also filteratuion and classification phase (104 ) by our system 
- and can also be used to distribute among the users (105)

In summary our system is always self aware what kind if sound file it is dealing provided that the inputs to system does not have any human errors





**Learning and Improving Based on the historical data**** 

We  are applying ML in almost every phases of the system such as ASR Engine ( third party), node detector,(11) Improvement by ML (12), text segmentation(103), Filtration/ Classification by Confidence Score , chunk distribution(105) . So there is always a continuous process of improvement at each phase of the system. 

As each generates a certain output and this output can be used to calculate errors made by different phases of the ML. thus providing a  constant feedback to the Learning algorithms  so that they can improve better.

Lets take  an example :



suppose the chunk given to transcription with LCS was :

The patient is a 45 year old male with a along history of insolent dependent 

and the chunk was transcribed by transciptionist

The patient is a 45 year old male with a **long** history of **insulin** dependent 

so we collect the data  what improvement was made by a human to correct the output of the given text 

thus kind of data feedback  is utilized to improve our ML algorithm so that next time our performs better.



So our system is constantly learning from it mistake by utilizing the manually corrected output  as a feedback to the system .