# -FILE-INTEGRITY-CHECKER
import hashlib
import os
import json

HASH_FILE = "file_hashes.json"

def calculate_hash(file_path):
    """Calculate SHA256 hash of a file."""
    sha256 = hashlib.sha256()
    try:
        with open(file_path, "rb") as f:
            while chunk := f.read(8192):
                sha256.update(chunk)
        return sha256.hexdigest()
    except FileNotFoundError:
        print(f"[ERROR] File not found: {file_path}")
        return None

def load_hashes():
    """Load stored file hashes from JSON file."""
    if os.path.exists(HASH_FILE):
        with open(HASH_FILE, "r") as f:
            return json.load(f)
    return {}

def save_hashes(hashes):
    """Save file hashes to JSON file."""
    with open(HASH_FILE, "w") as f:
        json.dump(hashes, f, indent=4)

def check_integrity(files):
    """Check if files are modified compared to stored hashes."""
    stored_hashes = load_hashes()
    new_hashes = {}
    for file in files:
        file_hash = calculate_hash(file)
        if file_hash:
            new_hashes[file] = file_hash
            if file in stored_hashes:
                if stored_hashes[file] != file_hash:
                    print(f"[ALERT] File modified: {file}")
                else:
                    print(f"[OK] File unchanged: {file}")
            else:
                print(f"[NEW] File added: {file}")
    save_hashes(new_hashes)

if __name__ == "__main__":
    # Example: Replace with your file paths
    files_to_monitor = ["example.txt", "data.csv"]
    check_integrity(files_to_monitor)
