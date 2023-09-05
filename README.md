# [Unveiling Electric Network Frequency from Events](https://xlx-creater.github.io/Improved_E-ENF/)

### [Project Page](https://xlx-creater.github.io/Improved_E-ENF/) | [Paper](https://arxiv.org/pdf/2305.02597.pdf) | [Data](https://whueducn-my.sharepoint.com/:f:/g/personal/2018302120267_whu_edu_cn/EkJtb2JNiWtJnASq_kckTZ8BAVymlOXmrEthItfKRVtGmA?e=RNNzez)

<img src='https://github.com/xlx-creater/E-ENF/blob/main/Illustration.png'/> 

> [Unveiling Electric Network Frequency from Events](https://xlx-creater.github.io/Improved_E-ENF/) 
>
>  [Lexuan Xu](https://scholar.google.com.hk/citations?hl=zh-CN&user=g3itm8IAAAAJ), [Guang Hua](https://ghua-ac.github.io/), [Haijian Zhang](https://scholar.google.com/citations?user=cEWbejoAAAAJ&hl=zh-CN&oi=ao), [Lei Yu](https://scholar.google.com/citations?user=Klc_GHUAAAAJ&hl=zh-CN).
>


## Prepare Data

Download the datasets from [EV-ENFD+](https://whueducn-my.sharepoint.com/:f:/g/personal/2018302120267_whu_edu_cn/EkJtb2JNiWtJnASq_kckTZ8BAVymlOXmrEthItfKRVtGmA?e=RNNzez).


1. Place one or several raw event files in the '.aedat4' format under the three scenarios in EV-ENFD into the 'Events/Raw/'.
2. Run 'Event_Process/aedat4_unpack_without_flir.py' to unpack '.aedat4' files in 'Raw', and the result will be saved in 'Events/Unpacked/dvSave-' (containing two folders: 'events' for unpacked events and 'event2ts' for frame-compressed event stream in time surface mode).
3. Replace 'Events/ENF_Reference' with the 'ENF_Reference' folder in EV-ENFD, where each '.wav' file contains grid voltage changes recorded by the transformer within an hour.


After performing the aforementioned operations, the contents of the 'Events' folder are as follows:
```
<project root>
  |-- Events
  |     |-- Raw
  |     |     |-- dvSave-2022_08_17_20_10_23.aedat4
  |     |     |-- dvSave-2022_08_17_20_24_41.aedat4
  |     |     |-- ...
  |     |-- Unpacked
  |     |     |-- dvSave-2022_08_17_20_10_23
  |     |     |    |-- events
  |     |     |    |-- event2ts
  |     |     |-- dvSave-2022_08_17_20_24_41
  |     |     |    |-- events
  |     |     |    |-- event2ts
  |     |     |-- ...     
  |     |-- ENF_Reference
  |     |     |-- 2022_08_17_Wed_17_00_00.wav
  |     |     |-- 2022_08_17_Wed_18_00_00.wav
```


## Estimate Electric Network Frequency using E-ENF

<img src='https://github.com/xlx-creater/Improved_E-ENF/blob/main/GUI.png' />

To use the GUI interface shown above, run 'E_ENF/E_ENF(GUI)/ENF_match_GUI.py' and follow these steps:

1. Click on the 'Unpacked Events' button and select the desired event stream from the 'Events/Unpacked/dvSave-/events' folder (e.g., 'dvSave-2022_08_17_20_10_23/events') for extraction.
2. Select the real ground truth reference by clicking on the 'ENF_Reference Folder' button and choosing the 'Events/ENF_Reference' folder.
3. Press the 'Start' button to initiate the estimation of the ENF signal from the selected event stream. The estimated result will be displayed in the middle of the GUI.


