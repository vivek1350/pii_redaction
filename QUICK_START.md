# PII Document Redactor - Quick Start Guide

## 🚀 Get Started in 30 Seconds

### Step 1: Open the Application
```
Open index.html in your web browser
(Chrome, Firefox, Safari, or Edge recommended)
```

### Step 2: Upload a Document
- **Option A**: Drag & drop a document onto the upload area
- **Option B**: Click "Choose Files" button
- **Supported formats**: PNG, JPG, PDF, TIFF, GIF, WebP
- **Max size**: 10 MB

### Step 3: Configure Detection (Optional)
In the Settings panel, toggle which PII types to detect:
- ✅ Social Security Numbers
- ✅ Credit Card Numbers
- ✅ Email Addresses
- ✅ Phone Numbers
- ✅ Dates & Expiry
- ✅ Full Names
- ✅ Addresses
- ✅ Date of Birth

Also choose redaction method:
- **Character Masking** (text replacement) - Default
- **Blur** (pixelated boxes) - For images

### Step 4: Process Document
Click the **"🔄 Process Document"** button

**Wait for processing** (5-35 seconds depending on image quality)
- You'll see a progress bar
- Status updates show current operation

### Step 5: Review Results
You'll see three panels:
1. **Original Document** - Your uploaded file
2. **Detected PII** - All sensitive information found
3. **Redacted Document** - Version with PII masked/blurred

Each detected item shows:
- **Type** - What kind of PII (e.g., Credit Card)
- **Original** - The actual value found
- **Masked** - How it appears when redacted
- **Confidence** - How sure the detection is

### Step 6: Download Results

Choose export format:

#### Option A: Download Redacted Image
```
Button: "⬇️ Download Redacted"
Format: PNG image file
Use: Print, email, or archive safely
```

#### Option B: Download Report
```
Button: "📊 Download Report"
Format: Text file (.txt)
Use: Audit trail and documentation
Includes: All detected PII with confidence scores
```

#### Option C: Export JSON
```
Button: "📋 Export JSON"
Format: JSON file (.json)
Use: Programmatic processing and integration
Includes: Raw data for analysis
```

## 📋 Common Use Cases

### Use Case 1: Redact a Contract
```
1. Upload contract.pdf
2. Keep all detection enabled
3. Click "Process Document"
4. Review redacted version
5. Download PNG
6. Share with partners
```

### Use Case 2: Anonymize a Form
```
1. Upload form_scan.png
2. Enable: Names, Addresses, Phone, Email
3. Disable: Date/Time
4. Process
5. Download report for compliance
```

### Use Case 3: Archive Financial Document
```
1. Upload bank_statement.jpg
2. Focus on: Card Numbers, Account Numbers
3. Use "Blur" redaction method
4. Download redacted image
5. Store in secure location
```

## ⚙️ Settings Explained

### Detection Options

**Social Security Numbers**
- Detects: 123-45-6789 or 123456789
- Confidence: 95%
- Masking: XXX-XX-6789

**Credit Card Numbers**
- Detects: 13-19 digit card numbers
- Confidence: 90%
- Masking: XXXX-XXXX-XXXX-3333
- Tip: Includes all card types (Visa, MC, Amex)

**Email Addresses**
- Detects: user@domain.com format
- Confidence: 98%
- Masking: j***n@example.com

**Phone Numbers**
- Detects: (555) 123-4567 and variants
- Confidence: 85%
- Masking: ***-***-4567
- Note: US format focused

**Dates & Expiry**
- Detects: MM/DD/YYYY format
- Confidence: 80%
- Masking: XX/XX/XXXX
- Includes: Credit card expiry dates

**Full Names**
- Detects: First Last name patterns
- Confidence: 75%
- Masking: F**** L****
- Note: May have false positives

**Addresses**
- Detects: Street address with ZIP code
- Confidence: 80%
- Masking: 123 Main St, XXXXX
- Note: US format focused

**Date of Birth**
- Detects: "DOB" followed by date
- Confidence: 90%
- Masking: DOB XX/XX/XXXX

### Redaction Methods

**Character Masking** (Default)
- Replaces sensitive text with asterisks or X's
- Example: john@example.com → j***@example.com
- Use for: Text documents, reports
- Benefit: Reversible, text still readable

**Blur/Pixelation**
- Creates visual blur boxes over sensitive areas
- Example: Black rectangles on document
- Use for: Image documents, photos
- Benefit: Visual proof of redaction

## 🔍 Understanding Results

### Statistics Panel
```
Total Found: 5          ← Total PII instances
Cards: 1                ← Credit card numbers
SSNs: 1                 ← Social Security Numbers
Contact: 3              ← Emails + Phone numbers
```

### Detected PII Entry
```
┌─────────────────────────────────────┐
│ CREDIT CARD NUMBER                  │ ← Type
│ Original: 4532-1111-2222-3333      │ ← What was found
│ → XXXX-XXXX-XXXX-3333             │ ← How it's masked
│ Confidence: 90%                    │ ← How sure
└─────────────────────────────────────┘
```

## 💡 Tips & Tricks

### For Better OCR Results
✅ Use high-resolution images (200+ DPI)
✅ Ensure document is well-lit
✅ Keep document straight (not rotated)
✅ Use PNG/JPG format (avoid GIF)
✅ Keep file size reasonable (< 5MB)

### For Accurate Detection
✅ Enable only needed detection types
✅ Review extracted text for OCR errors
✅ Manually verify important redactions
✅ Download JSON to see all findings
✅ Check confidence scores

### For Privacy
✅ Always use HTTPS connections
✅ Work in private/incognito browser window
✅ Clear browser history after processing
✅ Never share in-progress images
✅ Delete temporary files securely

## ⚠️ Important Notes

### What Happens to Your Data?
✅ **Everything stays on your device**
✅ No data sent to servers
✅ No cloud processing
✅ No storage or tracking
✅ Cleared when you close the browser

### Limitations
⚠️ OCR accuracy depends on image quality
⚠️ Some PII patterns may be missed
⚠️ Some false positives may occur
⚠️ Always review results before sharing
⚠️ Not 100% replacement for professional redaction

### Best Practices
1. **Always manually verify** redacted documents
2. **Keep backup** of original (secure storage)
3. **Test** with non-sensitive documents first
4. **Use HTTPS** for browser access
5. **Review** before distribution

## 🔧 Troubleshooting

### "Document won't upload"
- Check file format (PNG, JPG, PDF)
- Verify file size < 10MB
- Try another file
- Refresh browser

### "Processing takes too long"
- First run loads OCR models (~20-30 sec)
- Subsequent runs are faster (models cached)
- Try smaller file size
- Ensure browser not low on memory

### "PII not detected"
- Check that detection type is enabled
- Verify text is clear and readable
- Look at "Extracted Text" for OCR errors
- Some patterns have strict format requirements
- Try manual review

### "Browser seems slow"
- Close other browser tabs
- Clear browser cache
- Restart browser
- Try different browser
- Check system memory

## 📱 Mobile Use

### Supported Devices
✅ iPhone/iPad (Safari)
✅ Android phones (Chrome)
✅ Tablets (most browsers)

### Mobile Tips
- Larger files may be slow on older phones
- Mobile OCR can be slower (expect 20-40 sec)
- Landscape orientation recommended
- Test with small file first

## 📊 When to Use What

### Use Character Masking When:
- Working with text documents
- Need reversible redaction
- Want to show some context
- Creating reports

### Use Blur When:
- Working with image documents
- Want visual proof of redaction
- Sharing with non-technical users
- Want more obvious masking

### Download PNG When:
- Sharing redacted document
- Printing for distribution
- Archiving final version
- Email distribution

### Download Report When:
- Creating audit trail
- Documenting compliance
- Review findings details
- Share with reviewers

### Export JSON When:
- Programmatic processing
- Integration with other tools
- Data analysis
- Batch processing

## 🎯 Next Steps

1. **Practice** - Try with sample documents first
2. **Configure** - Set detection preferences for your use case
3. **Review** - Always verify results before sharing
4. **Integrate** - Consider workflow for regular use
5. **Automate** - Use JSON export for batch processing

## 📚 More Information

For detailed technical information:
- See **ARCHITECTURE.md** for system design
- See **README.md** for complete documentation
- Check browser console (F12) for error messages

## ✅ You're Ready!

You now know how to:
- ✅ Upload documents
- ✅ Configure detection settings
- ✅ Process documents
- ✅ Review results
- ✅ Export in multiple formats

**Start redacting now!** Open `index.html` in your browser.

---

**Version**: 1.0  
**Last Updated**: June 25, 2026
