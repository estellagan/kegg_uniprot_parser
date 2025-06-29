# kegg_uniprot_parser
A KEGG-to-UniProt annotation pipeline in Python code that processes multiple mouse pathway links from a designated file (saved as 'kegg_links.txt'), extracts protein IDs from KEGG (Mus musculus) pathways, maps reviewed UniProt IDs, retrieves subcellular localization data for each, and exports one annotated output file per pathway.

---

## Features
- Parses KEGG pathway maps for `mmu` (mouse) gene entries
- Extracts corresponding relevant **UniProt protein IDs**
- Queries the **UniProt REST API** for:
  - Review status, check if each entry is **reviewed** or not
  - Retrieve **subcellular location(s)** (if available)
- Skips **unreviewed** entries
- Condenses common location names (e.g., Cytoplasm → `Cy`, Mitochondria → `Mi`)
- Outputs one `.txt` file per pathway, named using the pathway title
- Supports **batch processing** via a plain `.txt` file of KEGG links

---

## Example Input File (kegg_links.txt)
  https://www.kegg.jp/pathway/mmu00290
  https://www.kegg.jp/pathway/mmu00300

## Example Output File
### **File 1**  
**Valine_leucine_and_isoleucine_biosynthesis.txt**  
UniProt_ID	Subcellular_Location(s)  
Q8VBT2	Cy  
Q8R238	https://www.uniprot.org/uniprot/Q8R238  
P24288	Cy  
O35855	Mi  
### **File 2**  
**Lysine_biosynthesis.txt**  
UniProt_ID	Subcellular_Location(s)  
Q9WVM8	Mi  
