# Case Title
Reconstructing File Activity from the $MFT (Draft)

## Objective
Reconstruct the activity on day1_test.txt (create, edit, copy, rename) using only the $MFT.

## Evidence
Files, images or logs analyzed (name, hash, source).
C:/Lab/day1_renamed.txt
C:/Users/mariem/AppData/Roaming/Microsoft/Windows/Recent/day1_test.lnk
C:/Lab/day1_test - Copy.txt
$MFT
mft.csv

## Tools Used
KAPE, MFTECmd and TimelineExplorer

## Methodology
1. Collected $MFT logs using KAPE
2. Converted it to a csv using MFTCmd
3. Opened the csv file using TimelineExplorer
4. Searched for the word "day1"

## Findings
What I found, with screenshots or command output.

## Timeline
Time | Event | Source artifact
10:30:09 | day1_renamed.txt created | Created0x10
10:30:21 | day1_test.lnk created | Created0x10
10:35:15 | day1_test.lnk modified and record changed | Last Modified0x10
10:36:44 | day1_renamed.txt modified and day1_test - Copy.txt record changed | Last Modified0x10 for day1_renamed.txt/ Last Record Change0x10 and Copied = 1 for day1_test - Copy.txt
10:38:14 | day1_test - Copy.txt created | Created0x10
10:38:30 | day1_renamed.txt record changed | Last Record Change0x10

## Conclusion
High confidence : File day1_renamed.txt creation, modification and record change. Why ? directly from timestamps.
Medium confidence: day1_renamed.txt was copied to day1_test - Copy.txt. Why ? Copied flag + exact same time of day1_renamed.txt modification and day1_test - Copy.txt record change 
Low confidence: day1_renamed.txt was initially day1_test.txt and got renamed at 10:38:30. Why ? the LNK file is named day1_test.lnk, the copy file is named day1_test - Copy.txt then day1_renamed.txt file's record changed after the copy file is created.
