## Py3Dmol Visualization — Code & Results
 
py3Dmol's output is a live WebGL canvas, not a static image, so it doesn't render here. Code is shown below; paste your screenshot in the placeholder right after each block. Replace `screenshot_X.png` with your actual image filename/path once you save it.
 
---
 
## 1. Ligand visualization: Nirmatrelvir (stick representation)
 
```python
import py3Dmol
 
nmt = py3Dmol.view(query='cid:155903259')  # Nirmatrelvir, PubChem CID 155903259
nmt.setStyle({'stick': {'color': 'spectrum'}})
nmt.show()
```
 
**Output:**
 
![Nirmatrelvir stick view](https://github.com/kush021104/protein-visulaisation-using-py3dmol/blob/main/Screenshot%202026-06-27%20173203.png)
 
---
 
## 2. Ligand visualization: Nirmatrelvir (stick + VDW surface)
 
```python
import py3Dmol
 
nmt = py3Dmol.view(query='cid:155903259')  # Nirmatrelvir, PubChem CID 155903259
nmt.setStyle({'stick': {'color': 'spectrum'}})
nmt.addSurface('VDW', opacity=0.5, colorScheme=('gradient', 'rwd'))
nmt.show()
```
 
**Output:**
 
![Nirmatrelvir with surface](https://github.com/kush021104/protein-visulaisation-using-py3dmol/blob/main/Screenshot%202026-06-27%20173231.png)
 
---
 
## 3. Protein visualization: SARS-CoV-2 Mᵖʳᵒ (cartoon representation)
 
```python
Mpro = py3Dmol.view(query='pdb:7RFS')  # SARS-CoV-2 main protease (M^pro)
Mpro.setStyle({'cartoon': {'color': 'spectrum'}})
Mpro.show()
```
 
**Output:**
 
![Mpro cartoon view](https://github.com/kush021104/protein-visulaisation-using-py3dmol/blob/main/Screenshot%202026-06-27%20173254.png)
 
---
 
## 4. Protein visualization: SARS-CoV-2 Mᵖʳᵒ (cartoon + VDW surface)
 
```python
Mpro = py3Dmol.view(query='pdb:7RFS')  # SARS-CoV-2 main protease (M^pro)
Mpro.setStyle({'cartoon': {'color': 'spectrum'}})
Mpro.addSurface('VDW', opacity=0.1, colorScheme=('gradient', 'rwd'))
Mpro.show()
```
 
**Output:**
 
![Mpro with surface](https://github.com/kush021104/protein-visulaisation-using-py3dmol/blob/main/Screenshot%202026-06-27%20173316.png)
 
---
 
## Notes on the JS rendering issue
 
py3Dmol depends on 3Dmol.js loading correctly in the notebook's JS runtime. If output didn't render, it's almost always one of these — worth checking before assuming it's unfixable:
 
- **Trust the notebook / re-run all cells.** On Jupyter, untrusted notebooks block embedded JS by default. `File → Trust Notebook`, then re-run.
- **Colab-specific:** py3Dmol's widget sometimes fails silently on first run in Colab — re-running the cell a second time after the library import often fixes it.
- **Internet connectivity at render time.** The view object fetches the structure live from PubChem/RCSB when `.show()` runs; a dropped connection mid-fetch gives a blank canvas with no error.
- **Browser console (F12) will show the actual JS error** if you want to diagnose rather than route around it — worth doing once so you know which of the above it actually was, instead of guessing.
 
