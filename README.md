# OrthologyScripts

## gff_longestCDSinfo.py

#### Run command: 
python3 gff_longestCDSinfo.py [gff file name] [output file name]
	
#### Description: 
This script has similar behaviour as the previous scripts. It identifies the longest CDS transcript from the gff annotation file. For each gene, it builds dictionaries for each mRNA/transcript feature within that gene. <br>
If there is more than mRNA, it can determine which mRNA has the longest CDS sequences within it. That one is the the longest transcript.

#### Output files: 

This script outputs information valuable for
<ul>
	<li> finding the longest transcript for each gene </li>
	<li> determine all the CDS locations for the longest transcript and their corresponding reading frames </li>
		<ul>
		<li> Each CDS has its start and stop as such: "start:stop" all the CDS are separated by a ";" <br> The reading frame has the same format. </li>
		</ul>
	<li> Outfile file has the 5 fields </li>
		<ul>
			<li> gene id: gene that the longest transcript belongs to </li>
			<li> cds id: cds id for the longest transcript. valuable for finding the gene id in the cds fasta file </li>
			<li> chrom: chromosome for that particular gene </li>
			<li> pos: list of CDS positions </li>
			<li> frame: reading frame for each CDS position </li>
		</ul>
</ul>


## updateproteome_withxp.py

#### Description:

This runs very similarly to make_new_proteome.py, but it parses a list and cross references your two files using XP numbers instead.

#### Run command: 
python3 updateproteome_withxp.py [protein file name] [list of longest transcript XP numbers] [desire output file name]



## gtf_longestCDSinfo.py

#### Run command: 
python3 gtf_longestCDSinfo.py [gtf file name] [output file name]

#### Description: 

Runs the same as gff_longestCDSinfo.py but is adjusted for the gtf format. 

#### Output file: 
The same as above. The main difference as that the gene id is not different from the transcript id.


## maps_getlongestcolumn.py

#### Run command: 

python3 maps_getlongestcolumn.py [CDS output map] [output file name]
#### Description: 

Uses string search to pull the second column for the CDS ID's. These CDS ID's are used to edit FASTA files.


## auto_gff_getinfo.sh

#### Run command: 
./auto_gff_getinfo.sh WITHIN DIRECTORY

#### Description: 

Created CDS maps automatically for a directory of .gff / .gtf files. Must be run inside	the directory of interest.
		
#### Output: 

Creates file names as [.gff/gtf file name.CDS.output] <br>

Note: The script will find all files that contain .gff or .gtf, so if this is re-run MAKE SURE to delete the CDS.output files.


## auto_create_txlist.sh
	
#### Run command: ./auto_gff_getinfo.sh WITHIN DIRECTORY

#### Description: 
Creates a list of ID's from the second column of CDS.output files within a directory.<br> Note: If you don't need the second, run maps_getlongestcolumn.py
by hand and edit the string search for a different column number.
