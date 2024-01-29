## Acquisition

The first pro-active step in any digital forensic investigation is that of [acquisition](terminology). The inherent problem with digital media is that it is readily modified; Even just by accessing files. For this reason analysts obtain a bit-copy of the media using specialist tools which stop modification occurring. Working from a copy is one of the fundamental steps to making a forensics investigation audit able and acceptable to a court.

Another fundamental part of the process is the ability to verify the accuracy of the evidence produced. Acquisition and [verification](terminology) are key concepts in preparing digital media for an investigation.

Prior to the availability of very large storage capacity the acquisition process usually consisted of creating a bit-perfect copy of the digital media evidence. This is usually conducted with the media connected to a write blocking device which stops it from being modified during the process. After being acquired, the physical media is placed in secure storage. The forensic analyst conducts the forensic investigation on the copy. The aim of working on a copy of the evidence is to leave the original media intact which allows for any evidence to be verified proven accurate at a later date.

##### Write blockers

[Write blockers](terminology) can take two forms: hardware or software. The hardware devices are more reliable, stopping all write commands from reaching the digital media. Software writer blockers are less reliable and tend to be proprietary.

##### Acquired media

Acquired media is usually refereed to as an "image", they are stored in a number of open and proprietary formats. The popular EnCase software employs a proprietary, compressible, "EnCase Evidence File Format" (EEFF). Other open formats such as RAW (i.e. a simple bit-copy) are used by programs such as "FTK Imager". 

During acquisition forensic tools create a verification hash of the media. This allows an analyst to later confirm that the image and its contents are accurate. For example: The EnCase evidence file format stores a hash for every 64k of data along with an appended md5 hash of the entire media.

## Analysis

The second stage of digital forensics is analysis. Analysis of digital media requires an instinct for rooting out evidence and the use of your intuition to connect the dots.

In the field of digital forensics, analysis can take two forms:
- **Evidence recovery:** Where the analyst identifies information relevant to the investigation and presents it in a neutral form.
- **Expert analysis** can vary wildly from simple factual conclusions to a more speculative assessment of what recovered evidence represents. In criminal cases the latter is generally avoided at the analyst level. By comparison in civil corporate investigation, the latter is more common. This is due to the fact that managers often do not have the technical understanding to draw conclusions that law enforcement personnel might have. When conducting an investigation it is important to remember who will be receiving the evidence you collect and performing an analysis that meets their requirements and needs.

## Reporting

Reporting is a key final phase of any investigation. A skilled investigator aims to balance the technical facts against their own analysis, while presenting it in layman terms. Writing a good report is often a skill hard one by forensic analysts because communicating complicated ideas in simple language is not always easy. How you report findings depends a lot of who will be reading it. For the most part it's easiest to assume the person reading any report has no technical knowledge at all and pitch it to them.

A common forensic report might include:
- Summary of findings
- Description of findings
- Explanation of terms such as "unallocated space" and "peer 2 peer" (an extended glossary)
