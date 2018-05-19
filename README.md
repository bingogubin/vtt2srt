# Convert  from *.vtt to *.srt with Python

## Getting Started

1. Open vtt2srt.ipynb with your JupyterNotebook
2. Put *.vtt in one directory
3. Modify *.vtt filespath in the 3rd line
4. Press "shift+Enter"

## Source Code

```python
import os
import codecs
path='C:\\Users\\Administrator\\Downloads\\'
files= os.listdir(path)
for file in files:
    if (not os.path.isdir(file)) and ("vtt" in file):
        filename_src = file
        filename_dst = file.split('.')[0] + '.srt'
        with open(path+filename_dst,'w') as file_object_dst: 
            with open(path+filename_src,'r') as file_object_src:
                i=1
                for line in file_object_src:
                    if ("WEBVTT") in line:
                        continue
                    if "-->" in line:
                        file_object_dst.write(str(i)+"\n")
                        i=i+1
                        file_object_dst.write(line)
                    else:
                        if i!=1:
                            file_object_dst.write(line)
```

## Demo

### *.vtt file

WEBVTT

00:00:00.520 --> 00:00:03.530
All right, so welcome to
the third tutorial session.

00:00:03.530 --> 00:00:06.170
This one's on generative
adversarial networks.

### *.srt file

1
00:00:00.520 --> 00:00:03.530
All right, so welcome to
the third tutorial session.

2
00:00:03.530 --> 00:00:06.170
This one's on generative
adversarial networks.
























