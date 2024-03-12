
# Traffic Classification Dataset for Deep Adaptation Network

## Abstract
This dataset contains the payload data of 19,180 network flows extracted from two articles: [Enhancing Encrypted Traffic Classification with Deep Adaptation Networks](https://doi.org/10.1109/lcn58197.2023.10223333) and Encrypted Traffic Classification through Deep Domain Adaptation Network with Smooth Characteristic Function. The network flows are classified into three categories: E-commerce, Video on-demand, and Interactive data, which are labeled as 0, 1, and 2, respectively. These categories are derived from 10 different applications, such as Ebay, Amazon, Alibaba, Facebook, Youtube, Tiki, Shopee, Thegioididong, Google Hangout Chat, and Google Hangout VoIP.


## Data collection
Our DAQUIC dataset consists of data collected at two different time intervals. The first interval spans three weeks in March 2018 and includes Youtube, Google Hangout Chat (Chat) and Google Hangout VoIP (VoIP). The second interval covers March to April 2023 and includes video streaming of Facebook (or FB for short) and e-commerce websites in Southeast Asia such as Shopee, Tiki, Thegioididong, Ebay, Amazon and Alibaba. We consider various types of applications such as Chat, VoIP, video streaming and e-commerce websites. We use multiple machines to deploy data capture of each application, each machine will use [selenium](https://www.selenium.dev/) for automation, [tshark](https://tshark.dev/) to capture data and save it in pcap format.

## Data processing

We remove the headers and retain only the payload data. We also add a flow_id column to identify the flow that each packet belongs to. We use 20 packets per flow for our analysis, and we discard flows with less than 500 packets as they are likely to be noise from background applications. The payload data is initially in hex code format, so we convert it to binary and divide it into bytes. Each byte is a column with 2 characters. After preprocessing, the data is organized in 20 consecutive rows for each flow, which represent 20 packets in that flow.

## Data structure

The data consists of two folders: `concat` and `concat_dataset`.

### concat

This folder contains the tabular data in feather format, which requires `pyarrow` and `pandas` libraries to open. This is the data we use for the proposed method.

The data is pre-divided into training, validation, and testing sets for source and target domains. The data is also pre-divided into different byte sizes: 10, 32, 64, 128, 256, 512, and 1024.

The file name structure is as follows:

```
<Data type>_<Domain>_<Byte size>.feather
```

Where:

- `<Data type>` is either `train` or `test`.
- `<Domain>` is either `source`, `target`, or `raw` (only for test and validation sets on the source domain).
- `<Byte size>` is one of the following values: 10, 32, 64, 128, 256, 512, 1024. If this part is omitted, it means all bytes are taken.

For example: train_source_256.feather, test_raw_256.feather

### concat_dataset

This folder contains the data that we use to run with other domain adaptation methods in the `tllib` [library](https://github.com/thuml/Transfer-Learning-Library). This data is pre-exported to images from a set of 256 bytes.

## Data access
The data is available for download from the [Google Drive](https://drive.google.com/drive/folders/15QHyWpBFvKztZASW-W-1Th4Oyd3Dtbpi?usp=sharing). The data is licensed under the Creative Commons Attribution 4.0 International License, which means you are free to share and adapt the data for any purpose, as long as you give appropriate credit, provide a link to the license, and indicate if changes were made. You may do so in any reasonable manner, but not in any way that suggests the licensor endorses you or your use. You may not apply legal terms or technological measures that legally restrict others from doing anything the license permits.
