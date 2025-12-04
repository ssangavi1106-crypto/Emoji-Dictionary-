1. VARIABLES & DATA TYPES
emoji_dict = {
    ":smile:": "😊", ":laugh:": "😂", ":heart:": "❤️", 
    ":fire:": "🔥", ":thumbs_up:": "👍", ":sad:": "😢"
}
user_file = "emojis.txt"
history = []  # List for history

# 2. FUNCTIONS (Regular & Lambda)
def convert_text_to_emoji(text):
    """Convert text with emoji codes to actual emojis"""
    words = text.split()
    output = ""
    for word in words:
        output += emoji_dict.get(word, word) + " "
    return output.strip()

emoji_lambda = lambda text: " ".join([emoji_dict.get(w, w) for w in text.split()])

def reverse_lookup(emoji_char):
    """Find emoji name from character (Dictionary iteration)"""
    for code, char in emoji_dict.items():
        if char == emoji_char:
            return code
    return "Emoji not found"

# 3. LIST COMPREHENSIONS & GENERATORS
emoji_list = list(emoji_dict.values())
emoji_codes = [k for k, v in emoji_dict.items()]
def emoji_generator():
    """Generator for lazy loading emojis"""
    for code, emoji in emoji_dict.items():
        yield f"{code} -> {emoji}"

# 4. FILE HANDLING
def save_history(text, result):
    """Save conversion history to file"""
    with open(user_file, "a", encoding="utf-8") as f:
        f.write(f"{text} -> {result}
")

def load_history():
    """Load history from file"""
    try:
        with open(user_file, "r", encoding="utf-8") as f:
            return f.readlines()
    except FileNotFoundError:
        return []

# 5. EXCEPTION HANDLING
def safe_convert(text):
    """Safe conversion with error handling"""
    try:
        result = convert_text_to_emoji(text)
        save_history(text, result)
        history.append((text, result))
        return result
    except Exception as e:
        return f"Error: {str(e)}"

# 6. CLASSES & OOP (Inheritance)
class BaseEmojiDict:
    def __init__(self):
        self.emojis = emoji_dict.copy()
    
    def add_emoji(self, code, emoji):
        self.emojis[code] = emoji

class EmojiConverter(BaseEmojiDict):
    def __init__(self):
        super().__init__()
    
    def batch_convert(self, texts):
        """Convert multiple texts"""
        return [self.convert_single(t) for t in texts]
    
    def convert_single(self, text):
        return convert_text_to_emoji(text)

# 7. DECORATORS
def log_usage(func):
    def wrapper(*args, **kwargs):
        print(f"Using {func.__name__}")
        return func(*args, **kwargs)
    return wrapper

@log_usage
def print_all_emojis():
    for code, emoji in emoji_dict.items():
        print(f"{code}: {emoji}")

# 8. MODULES & IMPORTS
import json
import re
from datetime import datetime

def export_json():
    """Export dictionary to JSON"""
    data = {"emojis": emoji_dict, "timestamp": str(datetime.now())}
    with open("emoji_export.json", "w", encoding="utf-8") as f:
        json.dump(data, f, ensure_ascii=False, indent=2)

# 9. REGULAR EXPRESSIONS
def find_emoji_codes(text):
    """Find emoji codes in text using regex"""
    pattern = r":w+:"
    return re.findall(pattern, text)

# 10. MAIN EXECUTION & CONTROL FLOW
if __name__ == "__main__":
    converter = EmojiConverter()
    
    # Demo all features
    print("=== EMOJI DICTIONARY DEMO ===")
    
    # User input & conversion
    user_input = input("Enter text with emoji codes (e.g. ':smile: :heart:'): ")
    result = safe_convert(user_input)
    print(f"Converted: {result}")
    
    # Reverse lookup
    emoji_char = input("Enter an emoji to find its code: ")
    code = reverse_lookup(emoji_char)
    print(f"Code: {code}")
    
    # Batch processing
    texts = ["Hello :smile:", ":fire: day!"]
    batch_results = converter.batch_convert(texts)
    print("Batch:", batch_results)
    
    # Show history
    print("
History:")
    for h in load_history()[-3:]:  # Last 3 entries
        print(h.strip())
    
    # Generator demo
    print("
All Emojis (Generator):")
    for item in emoji_generator():
        print(item)
    
    export_json()
    print_all_emojis()
