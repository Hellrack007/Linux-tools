### EasyNote by Hellrack007 github.com/Hellrack007
### A simple command-line note-taking application in Python.

import os
import sys


NOTES_DIR = os.path.expanduser("~/.config/easynote/notes")

# --- Funktionen ---
def add_note(note_text, name):
    os.makedirs(NOTES_DIR, exist_ok=True)
    if not name.endswith(".txt"):
        name += ".txt"
    filename = os.path.join(NOTES_DIR, name)
    try:
        with open(filename, "w") as f:
            f.write(note_text)
        print(f"Note saved as {filename}")
    except Exception as e:
        print(f"Error saving note: {e}")

def open_note():
    os.makedirs(NOTES_DIR, exist_ok=True)
    notes = sorted(os.listdir(NOTES_DIR))

    if not notes:
        print("No notes found to open.")
        return

    print("Available notes:")
    for idx, note in enumerate(notes, 1):
        print(f"{idx}. {note}")

    choice = input("Enter number OR filename: ").strip()

    if choice.isdigit():
        idx = int(choice) - 1
        if 0 <= idx < len(notes):
            filename = os.path.join(NOTES_DIR, notes[idx])
        else:
            print("Invalid number.")
            return
    else:
        
        if not choice.endswith(".txt"):
            choice += ".txt"

        filename = os.path.join(NOTES_DIR, choice)

        if not os.path.exists(filename):
            print("Note not found.")
            return
        
    os.system(f"nano '{filename}'")

def list_notes():
    os.makedirs(NOTES_DIR, exist_ok=True)
    notes = os.listdir(NOTES_DIR)
    if not notes:
        print("No notes found.")
        return
    print("Notes:")
    for note in sorted(notes):
        print(f" - {note}")

def show_help():
    print("EasyNote Usage:")
    print("  easynote 'Your note here'  Add a new note (add optional)")
    print("  easynote -l   |   --list                  List all notes")
    print("  easynote -h   |   --help          Show this help message")
    print("  easynote -o   |   --open                     Open a note")

if __name__ == "__main__":
    if len(sys.argv) < 2:
        show_help()
        sys.exit(0)

    cmd = sys.argv[1]

    if cmd in ("-h", "--help"):
        show_help()
    elif cmd in ("-l", "--list"):
        list_notes()
    elif cmd in ("open", "-o"):
        open_note()
    else:
        
        if cmd in ("add", "-a"):
            note_text = " ".join(sys.argv[2:])
        else:
            note_text = " ".join(sys.argv[1:])
        name = input("Enter filename: ").strip()
        add_note(note_text, name)
