# Case Title
Reconstructing File Activity from the $MFT (Draft)

## Objective
Reconstruct the activity on day1_test.txt (create, edit, copy, rename) using only the $MFT.

## Evidence
Files, images or logs analyzed (name, hash, source). <br>
C:/Lab/day1_renamed.txt <br>
C:/Users/mariem/AppData/Roaming/Microsoft/Windows/Recent/day1_test.lnk <br>
C:/Lab/day1_test - Copy.txt <br>
$MFT <br>
mft.csv <br>

## Tools Used
KAPE, MFTECmd and TimelineExplorer

## Methodology
1. Collected $MFT logs using KAPE <br>
2. Converted it to a csv using MFTCmd <br>
3. Opened the csv file using TimelineExplorer <br>
4. Searched for the word "day1" <br>

## Findings
Logs screenshots : <br>
1. <img src="images/Capture d'écran 2026-10-08 225446.png"></img>
2. <img src="images/Capture d'écran 2026-10-08 225459.png"></img>
3. <img src="images/Capture d'écran 2026-10-08 225513.png"></img>

## Timeline
Time | Event | Source artifact <br>
10:30:09 | day1_renamed.txt created | Created0x10 <br>
10:30:21 | day1_test.lnk created | Created0x10 <br>
10:35:15 | day1_test.lnk modified and record changed | Last Modified0x10 <br>
10:36:44 | day1_renamed.txt modified and day1_test - Copy.txt record changed | Last Modified0x10 for day1_renamed.txt/ Last Record Change0x10 and Copied = 1 for day1_test - Copy.txt <br>
10:38:14 | day1_test - Copy.txt created | Created0x10 <br>
10:38:30 | day1_renamed.txt record changed | Last Record Change0x10

## Conclusion
High confidence : File day1_renamed.txt creation, modification and record change. Why ? directly from timestamps. <br>
Medium confidence: day1_renamed.txt was copied to day1_test - Copy.txt. Why ? Copied flag + exact same time of day1_renamed.txt modification and day1_test - Copy.txt record change <br>
Low confidence: day1_renamed.txt was initially day1_test.txt and got renamed at 10:38:30. Why ? the LNK file is named day1_test.lnk, the copy file is named day1_test - Copy.txt then day1_renamed.txt file's record changed after the copy file is created. <br>
