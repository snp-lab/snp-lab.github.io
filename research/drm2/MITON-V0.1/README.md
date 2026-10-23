/*********************************************************
* Name: Malware I/O Traces On Nand flash (MITON)
* Version: 0.1 
* MITON is a dataset created in our project: 
* You can freely redistribute it and/or 
* modify it under the terms of the GNU General Public 
* License as published by the Free Software Foundation, 
* either version 3 of the License, or (at your option) any 
* later version.
* 
* MITON is distributed in the hope that it will be useful,
* but WITHOUT ANY WARRANTY; without even the implied 
* warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR 
* PURPOSE. See the GNU General Public License for more 
* details.
*
* Security and Privacy (SnP) Lab, Michigan Technological University
* https://snp.cs.mtu.edu

* This material is based upon work supported by the National Science Foundation under Grant Number 1938130:
* "EAGER: Enabling Secure Data Recovery for Mobile Devices against Malicious Attacks". Any opinions, findings,
* and conclusions or recommendations expressed in this material are those of the author(s) and do not 
* necessarily reflect the views of the National Science Foundation.
*********************************************************/ 

Each trace file is named using format: [family name]_[year]_[hash]

Each record in the trace file indicates an I/O on the flash memory using format: [0(reading) / 1(writing)], [starting logical page address], [length of consecutive pages in reading or writing].

How to generate the trace files?
We created a testbed consisting of open-source flash firmware, OpenNFM, an electronic board LPC-H3131 with 512MB NAND flash, and a host computer with Intel Core i7 8700K and 32GB RAM. The OpenNFM was ported to LPC-H3131, which can then be used as a regular flash-based block device via USB. OpenNFM contains 3 layers, FTL, UBI, and MTD. The FTL layer provides a few access interfaces including FTL_Read and FTL_Write, and we can capture each access caused by the upper layers by intercepting FTL_Read and FTL_Write. For each malware sample, we performed dynamic analysis by running it on the host computer, and collecting all its corresponding I/Os in the FTL into the corresponding trace file. Please refer to https://www.ieee-security.org/TC/SP2020/poster-abstracts/hotcrp_sp20posters-final11.pdf for more details.
