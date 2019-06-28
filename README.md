# kraken-ocr-greek_cursive
Training files for Greek cursive script (in early print)


Kraken was installed and used following the manual [Training a kraken model](http://kraken.re/training.html#training).

## Model for Savile
### Scans

The scans used are from exemplar of the edition of John Chrysostom's works by Henry Savile, ed. Eton (John Norton), Tom. V, 1612, which is today at Bayerische Staatsbibliothek München, Res/2 P.gr. 55-5, and was made available in digitized form at (http://mdz-nbn-resolving.de/urn:nbn:de:bvb:12-bsb10870413-4).

I used pp. 649–653 and 898–906. 

The scans downloaded were pre-processed with [ScanTailor](http://scantailor.org/) and are stored in the folder [savile](savile). Also stored in this folder is p. 92, both as the original color and as ScanTailor processed file. 


### Transcripts

The transcripts of the mentioned pages were taken from the [Patristic Text Archive](https://patristictextarchive.github.io) and converted to plain text ([savile-transcript.txt](savile-transcript.txt) with p. 649-653 and [savile-2-transcript.txt](savile-2-transcript.txt) with p. 898-906).

### Kraken training

Transcript files are saved as "output_XX.html" in the folders, the processed transcripts are in the folder [training](training).

```
$ ketos extract --output training --normalization NFD *.html
$ ketos train output_dir/*.png
$ ketos train training/*.png --threads 0                    
Building training set  [####################################]  100%          
Building validation set  [####################################]  100%          
[63.2770] alphabet mismatch {'6', '4', 'A', 'Λ', "'", ']', 'Ν', 'Ζ', '8', 'Ω', '9', '*', 'O', '[', 'I', 'o'} 
Initializing model ✓
stage 0/∞  [####################################]  521/521          
Accuracy report (520) 0.3358 5893 3914
stage 1/∞  [####################################]  521/521          
Accuracy report (1041) 0.7405 5893 1529
stage 2/∞  [####################################]  521/521          
Accuracy report (1562) 0.8407 5893 939
stage 3/∞  [####################################]  521/521          
Accuracy report (2083) 0.8967 5893 609
stage 4/∞  [####################################]  521/521          
Accuracy report (2604) 0.9196 5893 474
stage 5/∞  [####################################]  521/521          
Accuracy report (3125) 0.9381 5893 365
stage 6/∞  [####################################]  521/521          
Accuracy report (3646) 0.9486 5893 303
stage 7/∞  [####################################]  521/521          
Accuracy report (4167) 0.9513 5893 287
stage 8/∞  [####################################]  521/521          
Accuracy report (4688) 0.9530 5893 277
stage 9/∞  [####################################]  521/521          
Accuracy report (5209) 0.9574 5893 251
stage 10/∞  [####################################]  521/521          
Accuracy report (5730) 0.9579 5893 248
stage 11/∞  [####################################]  521/521          
Accuracy report (6251) 0.9545 5893 268
stage 12/∞  [####################################]  521/521          
Accuracy report (6772) 0.9628 5893 219
stage 13/∞  [####################################]  521/521          
Accuracy report (7293) 0.9632 5893 217
stage 14/∞  [####################################]  521/521          
Accuracy report (7814) 0.9656 5893 203
stage 15/∞  [####################################]  521/521          
Accuracy report (8335) 0.9678 5893 190
stage 16/∞  [####################################]  521/521          
Accuracy report (8856) 0.9644 5893 210
stage 17/∞  [####################################]  521/521          
Accuracy report (9377) 0.9681 5893 188
stage 18/∞  [####################################]  521/521          
Accuracy report (9898) 0.9703 5893 175
stage 19/∞  [####################################]  521/521          
Accuracy report (10419) 0.9686 5893 185
stage 20/∞  [####################################]  521/521          
Accuracy report (10940) 0.9683 5893 187
stage 21/∞  [####################################]  521/521          
Accuracy report (11461) 0.9691 5893 182
stage 22/∞  [####################################]  521/521          
Accuracy report (11982) 0.9695 5893 180
stage 23/∞  [####################################]  521/521          
Accuracy report (12503) 0.9715 5893 168
Moving best model model_9898.mlmodel (0.9703037502121161) to model_best.mlmodel
$ ketos test -m model_best.mlmodel training/*.png           
Loading model model_best.mlmodel	✓
Evaluating model_best.mlmodel
Evaluating  [####################################]  100%          
=== report  ===

57865	Characters
764	Errors
98.68%	Accuracy

509	Insertions
115	Deletions
140	Substitutions

Count	Missed	%Right
38199	346	99.09%	Greek
9518	113	98.81%	Common
10139	187	98.16%	Inherited
9	3	66.67%	Latin

Errors	Correct-Generated
71	{ ν } - {  }
51	{ SPACE } - {  }
46	{ COMBINING ACUTE ACCENT } - {  }
28	{  } - { SPACE }
27	{ α } - {  }
27	{ ι } - {  }
23	{ COMBINING GRAVE ACCENT } - { COMBINING ACUTE ACCENT }
21	{ COMBINING GRAVE ACCENT } - {  }
21	{ ε } - {  }
20	{ COMBINING COMMA ABOVE } - {  }
19	{ COMBINING ACUTE ACCENT } - { COMBINING GRAVE ACCENT }
19	{ τ } - {  }
16	{ COMBINING GREEK YPOGEGRAMMENI } - {  }
14	{ , } - {  }
14	{ υ } - {  }
14	{ COMBINING GREEK PERISPOMENI } - {  }
11	{  } - { COMBINING ACUTE ACCENT }
11	{ λ } - {  }
10	{ σ } - {  }
10	{ η } - {  }
10	{ ο } - {  }
9	{  } - { ν }
8	{ COMBINING DIAERESIS } - {  }
8	{ ω } - {  }
8	{ γ } - {  }
8	{ COMBINING REVERSED COMMA ABOVE } - {  }
8	{ π } - {  }
7	{  } - { υ }
7	{ μ } - {  }
6	{  } - { ι }
6	{ Ε } - { ε }
6	{  } - { COMBINING GRAVE ACCENT }
6	{ θ } - {  }
5	{  } - { ο }
5	{  } - { COMBINING COMMA ABOVE }
5	{ ρ } - {  }
5	{  } - { ε }
5	{ ς } - {  }
5	{ 6 } - {  }
5	{ θ } - { Θ }
5	{ κ } - {  }
4	{ . } - { · }
4	{ 9 } - {  }
4	{  } - { , }
4	{  } - { COMBINING GREEK PERISPOMENI }
4	{ · } - {  }
4	{ COMBINING COMMA ABOVE } - { COMBINING REVERSED COMMA ABOVE }
4	{  } - { . }
3	{ η } - { ο }
3	{ 5 } - {  }
3	{ υ } - { ο }
3	{ Τ } - { τ }
3	{ ζ } - {  }
3	{ . } - {  }
2	{ η } - { ε }
2	{ ο } - { ε }
2	{  } - { ρ }
2	{ - } - {  }
2	{ ε } - { ο }
2	{ τ } - { π }
2	{ COMBINING GREEK PERISPOMENI } - { COMBINING ACUTE ACCENT }
2	{ α } - { ε }
2	{  } - { COMBINING REVERSED COMMA ABOVE }
2	{  } - { τ }
2	{ ’ } - { COMBINING GRAVE ACCENT }
2	{ Δ } - { δ }
2	{ &#34; } - {  }
2	{ φ } - {  }
2	{  } - { δ }
2	{  } - { π }
2	{ COMBINING GRAVE ACCENT } - { COMBINING REVERSED COMMA ABOVE }
2	{ · } - { . }
2	{ Ο } - { ο }
2	{ , } - { . }
1	{ A } - { Α }
1	{ ν } - { τ }
1	{  } - { μ }
1	{  } - { Ι }
1	{ Θ } - {  }
1	{ Β } - {  }
1	{ σ } - { τ }
1	{ . } - { ; }
1	{ τ } - { ρ }
1	{ μ } - { κ }
1	{ σ } - { ς }
1	{  } - { ς }
1	{ Θ } - { θ }
1	{ 0 } - {  }
1	{ I } - { Ι }
1	{ Κ } - { κ }
1	{ ω } - { ο }
1	{ γ } - { COMBINING ACUTE ACCENT }
1	{ α } - { ’ }
1	{ ι } - { υ }
1	{ ς } - { COMBINING GRAVE ACCENT }
1	{ π } - { κ }
1	{ π } - { σ }
1	{  } - { η }
1	{ ’ } - { ρ }
1	{ σ } - { ν }
1	{  } - { Π }
1	{ SPACE } - { ι }
1	{ 2 } - {  }
1	{ δ } - {  }
1	{ ψ } - {  }
1	{ χ } - {  }
1	{ γ } - { δ }
1	{ ε } - { α }
1	{  } - { Α }
1	{ τ } - { ι }
1	{ ε } - { COMBINING COMMA ABOVE }
1	{ σ } - { ε }
1	{ ω } - { COMBINING GRAVE ACCENT }
1	{  } - { COMBINING GREEK YPOGEGRAMMENI }
1	{  } - { &#34; }
1	{ κ } - { ο }
1	{ COMBINING REVERSED COMMA ABOVE } - { COMBINING GRAVE ACCENT }
1	{ ’ } - {  }
1	{ ; } - { . }
1	{ σ } - { α }
1	{ 1 } - {  }
1	{ 0 } - { 5 }
1	{ &#39; } - { · }
1	{ Π } - { Ι }
1	{ ο } - { ω }
1	{ SPACE } - { &#34; }
1	{ &#39; } - {  }
1	{ ς } - { σ }
1	{  } - { α }
1	{ Ρ } - {  }
1	{ ν } - { ο }
1	{  } - { - }
1	{ τ } - { σ }
1	{ COMBINING GRAVE ACCENT } - { COMBINING GREEK PERISPOMENI }
1	{  } - { Ο }
1	{ · } - { , }
1	{ o } - { ο }
1	{ 2 } - { 1 }
1	{ ε } - { ι }
1	{ 2 } - { 0 }
1	{ COMBINING GREEK PERISPOMENI } - { COMBINING GRAVE ACCENT }
1	{ COMBINING REVERSED COMMA ABOVE } - { COMBINING COMMA ABOVE }

Average accuracy: 98.68%, (stddev: 0.00)
```
#### Results

The model was tested with both the color scan and the ScanTailor-processed scan with better results when the ScanTailor-processed scan is used.

```
$ kraken -i savile/savile-test.tif savile-test_2.txt binarize segment ocr -m model_best.mlmodel 

Loading RNN default	✓
Binarizing	✓
Segmenting	✓
Processing  [####################################]  100%          
Writing recognition results for /tmp/tmpljt5rmh2	✓
```

Test scan: [savile/savile-test.tif](savile/savile-test.tif) -> Text: [savile-test_2.txt](savile-test_2.txt)

```
$ kraken -i savile/savile-test-scantailor.tif savile-test_2-scantailor.txt binarize segment ocr -m model_best.mlmodel

Loading RNN default	✓
Binarizing	✓
Segmenting	✓
Processing  [####################################]  100%          
Writing recognition results for /tmp/tmp20fhsm8t	✓
```

Test scan: [savile/savile-test-scantailor.tif](savile/savile-test-scantailor.tif) -> Text: [savile-test_2-scantailor.txt](savile-test_2-scantailor.txt)


#### Model

The best model is saved as [model_grc_savile.mlmodel](model_grc_savile.mlmodel).

## Model for Catena Lipsiensis

### Scans

The scans used are from exemplar of ΣΕΙΡΑ ΕΝΟΣ ΚΑΙ ΠΕΝΤΗΚΟΝΤΑ ΥΠΟΜΝΗΜΑΤΙΣΤΩΝ ΕΙΣ ΤΗΝ ΟΚΤΑΤΕΥΧΟΝ ΚΑΙ ΤΑ ΤΩΝ ΒΑΣΙΛΕΙΩΝ ΗΔΗ ΠΡΩΤΟΝ ΤΥΠΟΙΣ ΕΚΔΟΘΕΙΣΑ ... ΓΡΗΓΟΡΙΟΥ ΑΛΕΞΑΝΔΡΟΥ ΓΚΙΚΑ, ΤΟΜΟΣ ΠΡΩΤΟΣ, Leipzig 1772, which is today at Philipps Universität Marburg,  shelfmark: XIXb A 371 c, 1, and was made available in digitized form at http://archiv.ub.uni-marburg.de/eb/2011/0432.

I used pp. 953–976. 

The scans downloaded were pre-processed with [ScanTailor](http://scantailor.org/) and are stored in the folder [catenalipsiensis](catenalipsiensis). 

### Transcripts

The transcripts of the mentioned pages were made by Janina Skóra and converted to plain text ([Catena_Lispiensis.txt](Catena_Lipsiensis.txt)). The transcription files for kraken are also stored in the folder [catenalipsiensis](catenalipsiensis).

### Model

The best model is saved as [model_grc_catlips.mlmodel](model_grc_catlips.mlmodel).
