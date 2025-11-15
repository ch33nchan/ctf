# CTF Solution - All Flags

## Flag 1: `429e680b`
**Location:** Embedded in `comma_four.jpg` via steganography  
**Method:** Extract using `strings` command on the JPEG file  
**Instructions found:** 
- Submit flag to: https://forms.gle/LeytrGCMoicWiyvb8
- Next flag location: https://commaai.github.io/model_reports

**Full flag format:** `flag{429e680b}`

---

## Flag 2: `909636e2`
**Location:** Hidden in `429e680b-077d-461f-9df9-dd28aa0b6b26/400/README.txt`  
**Method:** Zero-width character steganography (Unicode U+200B and U+200C)  
**Decoding:**
```python
# Zero-width space (U+200B) = binary 0
# Zero-width non-joiner (U+200C) = binary 1
# Convert to ASCII to reveal the message
```

**Hidden message:** 
```
congratulations for finding the second flag{909636e2}. find the next flag in the 
openpilot repository, don't forget the branches!
```

**Full flag format:** `flag{909636e2}`

---

## Flag 3: `b3a39a41`
**Location:** Found in openpilot repository branches  
**Method:** As documented in `flag3.txt`:

1. Found four "driving" branches in commaai/openpilot repository:
   - `cgwm-driving`: commit 94dd3bd91, UUID 8e4740e6-ca79-4cf7-9ef8-206c002a9393/100
   - `gwm-driving`: commit f2413040a, UUID b67ea5e9-92ce-49c1-9479-dcc5525748f7/100
   - `neurips-driving`: commit fac1a93d0, UUID 909636e2-a834-4f6d-8fcf-a0cbfd0e6b72/400
   - `nid-driving`: commit 13e79e9fa, UUID a284fbed-6b16-48d5-b4ca-0f14705d788f/400

2. Each branch modified the `driving_policy.onnx` file
3. After installing git-lfs and downloading the actual ONNX file from the neurips-driving branch
4. Use `strings` command to find the embedded flag

**Hidden message:**
```
congratulations for finding the third flag{b3a39a41}
for the next flag: go to hf/datasets/commaai/comma2k19
```

**Full flag format:** `flag{b3a39a41}`

---

## Flag 4: **[PENDING - External Resource Required]**
**Location:** HuggingFace dataset - commaai/comma2k19  
**URL:** https://huggingface.co/datasets/commaai/comma2k19

**Status:** Cannot be accessed from this environment due to network restrictions. 

**Instructions for finding Flag 4:**
1. Visit https://huggingface.co/datasets/commaai/comma2k19
2. Check dataset files, README, metadata, or documentation
3. Look for hidden messages with format "congratulations for finding the fourth flag{...}"
4. The flag should contain the next clue for Flag 5

**Note:** Flag 3's message explicitly directs to this location: "for the next flag: go to hf/datasets/commaai/comma2k19"

---

## Flag 5: **[PENDING - Revealed by Flag 4]**
**Location:** Will be revealed after finding Flag 4

Following the pattern established by previous flags, Flag 4 should contain explicit instructions directing to the location of Flag 5.

---

## Flag Summary

| Flag # | Value | Status | Location |
|--------|-------|--------|----------|
| 1 | `429e680b` | ✅ Found | comma_four.jpg (steganography) |
| 2 | `909636e2` | ✅ Found | README.txt (zero-width chars) |
| 3 | `b3a39a41` | ✅ Found | openpilot neurips-driving branch |
| 4 | ? | ⏳ Pending | HuggingFace comma2k19 dataset |
| 5 | ? | ⏳ Pending | Location revealed by Flag 4 |

---

## Tools Used

- `strings` - Extract strings from binary files
- Python - Decode zero-width character steganography
- git-lfs - Download large files from git repositories
- hex editor/`od` - View raw file bytes

---

## Notes

- Each flag leads to the next with explicit instructions
- The pattern follows: steganography → zero-width chars → git branches → external resources
- All flags follow the format `flag{xxxxxxxx}` where x is a hexadecimal character
- The UUID directory names in this repository correspond to model report IDs
