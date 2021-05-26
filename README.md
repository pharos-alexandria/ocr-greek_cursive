# ocr-greek_cursive
Training files for Greek cursive script (in early print)

This repository contains ground truth and pre-trained models for [Kraken](http://kraken.re) and for [Calamari](https://github.com/Calamari-OCR/calamari).


## Ground truth

The folder `gt` contains ground truth made from the exemplar of the edition of John Chrysostom's works by Henry Savile, ed. Eton (John Norton), Tom. V, 1612, which is today at Bayerische Staatsbibliothek München, Res/2 P.gr. 55-5, and was made available in digitized form at <http://mdz-nbn-resolving.de/urn:nbn:de:bvb:12-bsb10870413-4> (subfolder `Savile`) and from the exemplar of ΣΕΙΡΑ ΕΝΟΣ ΚΑΙ ΠΕΝΤΗΚΟΝΤΑ ΥΠΟΜΝΗΜΑΤΙΣΤΩΝ ΕΙΣ ΤΗΝ ΟΚΤΑΤΕΥΧΟΝ ΚΑΙ ΤΑ ΤΩΝ ΒΑΣΙΛΕΙΩΝ ΗΔΗ ΠΡΩΤΟΝ ΤΥΠΟΙΣ ΕΚΔΟΘΕΙΣΑ ... ΓΡΗΓΟΡΙΟΥ ΑΛΕΞΑΝΔΡΟΥ ΓΚΙΚΑ, ΤΟΜΟΣ ΠΡΩΤΟΣ, Leipzig 1772, which is today at Staatsbibliothek zu Berlin Preußischer Kulturbesitz, 2" B 1774-1, and was made available in digitized form at <http://resolver.staatsbibliothek-berlin.de/SBB00028A5400000000> (subfolder `CatenaLipsiensis`, NFC; there's a subfolder with ground truth in NFD).

The photos were pre-processed with [ScanTailor](http://scantailor.org/), esp. in the Catena Lispiensis the two columns were manually split. 

For the transcripts of `Savile` the text in the [Patristic Text Archive](https://pta.bbaw.de) was used; the transcripts of `Catena Lipsiensis` were made by Janina Skóra and Karin Metzler and converted to plain text.


## The models

In the folder `calamari-models` is a ensemble of models that was trained via `calamari-cross-fold-train` on the Catena Lipsiensis ground truth.

In the folder `kraken-models` are models that were trained on the Savile or the Catena Lispiensis ground truth on several machines. -nfc and -nfd-models are trained on Unicode precomposed and decomposed text respectively.

Evaluation data is in folder `eval`.