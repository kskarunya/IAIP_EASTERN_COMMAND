# ⚙️ Magazine Production Workflow

Follow these steps in exact order to generate the 45-page magazine.

## Phase 1: Data Collection & Structuring
1. **Run the Scraper:** Execute the SerpApi script using the provided region-locked Boolean queries (e.g., `"Indian Army" AND ("Northeast" OR "Assam"...)`). This creates `Northeast_Army_News_Bulk.csv`.
2. **Filter & Structure:** Run the structuring script to drop duplicate URLs and extract exactly 45 articles (distributed across your 5 chapters/categories). Output: `Magazine_45_Pages_Structured.csv`.

## Phase 2: Text Processing & NLP Summarization
1. **NLP Extraction:** Run the `sumy` summarization script. This analyzes the `Original Text` and creates:
   * `In Brief`: Extracts the single most important sentence.
   * `The Story`: Extracts the top 12 most relevant sentences.
   * `Key Fact`: Extracts a top sentence containing numerical data.
2. **Split for 2-Column Layout:** Run the splitting script to mathematically divide `The Story` column into `Column 1` and `Column 2` (preventing Canva text box overflow). Output: `Magazine_50_Pages_NLP_Layout.csv`.

## Phase 3: Image Formatting
1. **Fetch Images:** Run the image script to find article thumbnails.
2. **Rename Header:** Ensure the CSV column header for images is named exactly **`@Image URL`**. This critical step tells Canva to render the link as a photo inside an Image Frame, rather than raw text. Output: `Magazine_45_Pages_Final_Images.csv`.

## Phase 4: Canva Preparation
Canva's Bulk Create applies every row to every layout. To use 3 different layouts for 45 pages, we must split the data.
1. **Split the CSV:** Run `division_bulk.ipynb` to divide the master CSV into three separate files:
   * `Canva_Layout_1_Data.csv` (15 articles)
   * `Canva_Layout_2_Data.csv` (15 articles)
   * `Canva_Layout_3_Data.csv` (15 articles)

## Phase 5: Canva Bulk Generation
1. **Open Master Template:** Ensure your template has 3 pages (Layout A, B, and C).
2. **Configure Placeholders:** 
   * Ensure text boxes have **"Fit text to box / Shrink text on overflow" turned OFF**.
   * Ensure text boxes do not physically overlap on the canvas.
   * Ensure images are connected to **Frames** (from the Elements tab), not Shapes or Text boxes.
3. **Generate Layout 1:** Delete Pages 2 & 3. Upload `Layout_1_Data.csv`, map the fields, and hit Generate. Leave the new tab open.
4. **Generate Layout 2:** Undo the deletion. Delete Pages 1 & 3. Upload `Layout_2_Data.csv`, map fields, and Generate. 
5. **Generate Layout 3:** Undo deletion. Delete Pages 1 & 2. Upload `Layout_3_Data.csv`, map fields, and Generate.
6. **Merge:** Copy the generated pages from the Layout 2 and 3 tabs, and paste them into the Grid View of the Layout 1 tab. Add the Cover Page to the front.

## Phase 6: Finalizing Appendices
1. **Generate Sources:** Run `Appendices.ipynb`. This reads your final CSV and creates `Appendix_B_References.txt`.
2. **Insert into Canva:** Add two blank pages at the end of your merged Canva document. Paste the static Glossary into the first, and the generated Source Directory into the second.
3. **Export:** Export the final document as **PDF Standard** or **PDF Print**.
