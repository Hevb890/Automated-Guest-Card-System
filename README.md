# Automated-Guest-Card-System

## Description

Automated-Guest-Card-System is a Python-based utility designed to bridge high-fidelity wedding invitation design with modern digital distribution. This tool automates the generation of personalized guest cards from a static JPEG template and an Excel guest list.

## Features

- **Dynamic Image Synthesis:** Seamlessly overlay guest names onto a high-quality JPEG template using the Pillow library.
- **Precision Typography:** Supports right-alignment within custom-defined bounding boxes to ensure names fit perfectly regardless of length.
- **Bulk Generation:** Processes your entire guest list in one run, generating a uniquely named invite image per guest.
- **Auto Output Folder:** Automatically creates the output directory if it doesn't exist.

## Prerequisites

- Python 3.8+
- pip

### Install Dependencies (For MacOS)

```bash
python3 -m venv venv
```

```bash
. venv/bin/activate
```

```bash
pip3 install -r requirements.txt
```

Select the Created Virtual Environment Before running the script.ipynb

## Project Structure

```
/
├── main.py                # The primary automation script
├── Names.xlsx             # Excel file with a 'Names' column containing guest names (You need to add this)
├── Base.jpg               # Your high-res JPG card template (You need to add this)
├── Cormorant-Bold.otf     # Your chosen typography/calligraphy font (You need to add this)
└── Invitees/              # Generated output folder (auto-created)
```

## Configuration

At the top of `main.py`, adjust these constants to match your setup:

| Variable        | Default                   | Description                                        |
| --------------- | ------------------------- | -------------------------------------------------- |
| `PSD_PATH`      | `Base.jpg`                | Path to your invitation template image             |
| `EXCEL_PATH`    | `Names.xlsx`              | Path to your guest list Excel file                 |
| `FONT_PATH`     | `Cormorant-Bold.otf`      | Path to your chosen `.ttf` or `.otf` font file     |
| `OUTPUT_FOLDER` | `./Invitees`              | Directory where generated cards will be saved      |
| `FONT_SIZE`     | `60`                      | Font size for the guest name text                  |
| `TEXT_COLOR`    | `(0, 0, 0)`               | Text color as an RGB tuple (default: black)        |
| `box_coords`    | `[100, -100, 1320, 1400]` | Bounding box `[x1, y1, x2, y2]` for text placement |

### Bounding Box

The `box_coords` list defines the rectangular region where the guest name is placed:

```python
box_coords = [x1, y1, x2, y2]
```

- The name is **right-aligned** to `x2`.
- The name is **vertically centered** between `y1` and `y2`.

## Usage

1. Place `Base.jpg`, `Names.xlsx`, and your font file in the same directory as `main.py`.
2. Populate `Names.xlsx` with a column named **`Names`** containing each guest's full name.
3. Run the script:

```bash
script.ipynb
```

4. Find all generated invite cards in the `./Invitees/` folder, named in the format:

```
Mr._John_Smith_invite.jpg
```

## Excel Format

Your `Names.xlsx` should have a single column with the header `Names`:

| Names                    |
| ------------------------ |
| Mr. Asela Amaradiwakara  |
| Ms. Sahani Dissanayake   |
| Mr. & Mrs. Karunathilaka |

## Output Example

Each card is saved as a JPEG with the guest's name rendered directly on the template:

```
Invitees/
├── Mr._Asela_Amaradiwakara_invite.jpg
├── Ms._Sahani_Dissanayake_invite.jpg
└── Mr._&_Mrs._Karunathilaka_invite.jpg
```

## Tips

- **Font pairing:** Serif and calligraphy fonts (e.g., Cormorant, Playfair Display) work best for formal invitations.
- **Positioning:** Open one generated card and inspect the name placement before running the full batch. Adjust `box_coords` and `FONT_SIZE` as needed.
- **Long names:** The right-alignment logic automatically handles variable name lengths — longer names extend leftward from `x2`.

## License

This project is for personal use. Feel free to adapt it for your events.
