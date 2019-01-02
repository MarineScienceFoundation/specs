# Tech Specifications
![](media-artifacts/MSF_Fishsmall.png)
> This repository contains the specs for Marine Science Foundation projects and associated subsystems.

# Abstract
The underlying motivation for these project is to make collecting, storing, disemmination, and verification of scientific data easy. Data can be easily manipulated when source data is private, or worse cherry-picked. We are expecting to collect and generate large amounts of scientific data. Data storage and digitial data rot is a problem we are tackling before collecting any data. [OpenData](#OpenData) refers the the overall goals regarding collection and dissemination. [SeriesData](#SeriesData) is a particular implementation for sample based data collection and immutability. We will use a simple example of a weather station data to provide an example and methodology. 

## Table of Contents

- Works In Progress
- [Specs](#specs)
  - [Open Data Concepts](#OpenData): Overarching Data Handling Guidance
    - [OpenData Repo](https://github.com/MarineScienceFoundation/SeriesData)
  - [Series Data](#SeriesData): Example implementations for sample data
    - [SeriesData Repo](https://github.com/MarineScienceFoundation/SeriesData)
  - [libp2p](https://github.com/libp2p/specs): IPFS based library, Concepts important to project 
    - [IPRS](https://github.com/libp2p/specs/blob/master/IPRS.md)
- [Contribute](#contribute)
- [License](#license)

## Works In Progress Specifications
[![](https://img.shields.io/badge/made%20by-Marine%20Science%20Foudation-blue.svg?style=flat-square)](http://github.com/MarineScienceFoundation)

**Specs are not finished yet. We use the following tag system to identify their state:**

- ![](https://img.shields.io/badge/status-wip-orange.svg?style=flat-square) - this spec is a work-in-progress, it is likely not even complete.
- ![](https://img.shields.io/badge/status-draft-yellow.svg?style=flat-square) - this spec is a rough draft and will likely change substantially.
- ![](https://img.shields.io/badge/status-reliable-green.svg?style=flat-square) - this spec is believed to be close to final. Minor changes only.
- ![](https://img.shields.io/badge/status-stable-brightgreen.svg?style=flat-square) - this spec is likely to improve, but not change fundamentally.
- ![](https://img.shields.io/badge/status-permanent-blue.svg?style=flat-square) - this spec will not change.
## Specs 
![](https://img.shields.io/badge/status-wip-orange.svg?style=flat-square) 
## OpenData 
![](https://img.shields.io/badge/status-wip-orange.svg?style=flat-square) 
- Data should be accessable equally by all users. 
- Access to data should be free in most cases
- All pay the same, IPFS and Filecoin should fix this
- Data needs to be verifiable and referenceable 

## SeriesData 
![](https://img.shields.io/badge/status-wip-orange.svg?style=flat-square)

Series data is defined as data that is collected in a monotonic fashion. The data set may have any number of entries, but specific order matters. Interpreting data by selecting (cherry picking) data to get desired outcomes is considered bad science. Additionally, manipulating data by smoothing, biasing, etc can also cause great controversy. At MSF we are trying to bring accountability to data mashing for scientists. Both the data producers and the data users. We are building on years of Public Key Cryptography, IPFS technology, and Block Chain tools. 

In the simplest case. A scientist would register on IPFS for an address as a reference for building reputation on. The scientist would then use a proof of transaction on a Block Chain such as Bitcoin or Etherum to establish an identity for themselves, an experiment, or sensor. In the case of a sensor, the transaction would establish the initial measurement using a nonce included in the transaction. This can be thought of as a genesis code or has for the identity. 

Next the identity needs to post a measurement, paper, or other piece of data. The genesis code is used to prepend the data in question, a cryptographic hash is then unsed to close the data entry. in the format:
<p>
<code>
  Genesis hash, data to be added, Crypto-hash of (Genesis + data-to-be-added)
  Previous-Crypto-Hash, new data to be added, Crypto-Hash (Previous-Crypto-Hash, new data to be added) 
  ... 
</code>
</p>
 
This pattern goes on until a proof-of-transaction can be added to the list. The proof-of-transaction hash is called Transaction-Hash 

[Merkle Tree] This is were a link about MerkleTrees and proof of order comes in. 

The particular Hash is not called out, so that as exploits or weaknesses in a particular hash functions are found new hash-functions can be easily inserted. This is following in the [IPFS](ipfs.io) example.  

It is most easily understood as time series data. The order of the data collected is extremely important to the meaning of the data. 

- Data is assumed to be collected in samples/record
- Samples are not DSP samples, but small data blobs. 
- Initial work will be done on comma separated values (CSV) 
  - Sample/record in this case in one line in the CSV. 
- Each Sample/record is verified with a cryptographic hash
- This first sample is considered the genesis record. It needs some special properties
  - Information regarding the originator
    - Public Key - Originator: For Location and Signature
    - Public Key - Sensor: Optional
    - Data Storage Location
  - Time hack 
    - New Project 
  - Sensor Information
    - Examples:
    - Geolocation
    - Manufacture
    - Website
    - Data Storage Format
    
## Contribute

Suggestions, contributions, criticisms are welcome. Though please make sure to familiarize yourself deeply with the Marine Science Foundation, the models it adopts, and the principles it follows.

Please be aware that specs are really hard to design by committee. Treat this space like you would the workshop of an artist. Please suggest improvements, but please don't be disappointed if we say no to something. What we leave out is often more important than what we add in.

## License
TBD, IPFS seems to have converged on CC-BY
