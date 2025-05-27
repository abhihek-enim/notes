# 🧠 Linux Stage 1: Basic Commands & Usage

## 📂 Navigation Commands

### `pwd` - Print Working Directory
```bash
pwd
# Shows current working directory, e.g., /home/user/projects
```

### `ls` - List Directory Contents
```bash
ls
ls -l       # Long listing format
ls -a       # Includes hidden files
ls -lh      # Human-readable file sizes
ls -alh     # Combine all options
```

### `cd` - Change Directory
```bash
cd /etc             # Go to /etc
cd ..               # Go up one level
cd ~                # Go to home directory
cd ~/Documents      # Navigate using absolute path
```

### `tree` - Visual Directory Tree
```bash
tree               # Shows directory tree
sudo apt install tree  # Install if not found
```

---

## 📁 File/Directory Manipulation

### `touch` - Create Empty File
```bash
touch notes.txt
```

### `mkdir` - Make Directory
```bash
mkdir projects
mkdir -p a/b/c     # Create nested directories
```

### `cp` - Copy Files or Directories
```bash
cp file.txt backup.txt
cp -r src/ dest/   # Recursively copy directories
```

### `mv` - Move/Rename Files
```bash
mv file.txt ~/Documents/
mv old.txt new.txt   # Rename
```

### `rm` - Remove Files/Directories
```bash
rm file.txt
rm -r folder/       # Recursively remove directory
rm -rf folder/      # Forcefully and recursively remove (dangerous!)
```

### `rmdir` - Remove Empty Directory
```bash
rmdir empty_folder/
```

---

## 📄 Viewing File Content

### `cat` - Show File Contents
```bash
cat file.txt
```

### `less` / `more` - Paginated View
```bash
less largefile.txt
more largefile.txt
```

### `head` / `tail` - View Top/Bottom Lines
```bash
head -n 10 file.txt   # First 10 lines
tail -n 5 file.txt    # Last 5 lines
```

### `nl` - View with Line Numbers
```bash
nl file.txt
```

---

## 🔍 Search & Filter

### `grep` - Pattern Searching
```bash
grep "error" logfile.txt
grep -i "fail" *.log    # Case-insensitive search in all logs
```

### `find` - Search Files
```bash
find . -name "*.sh"             # Find shell scripts in current dir
find /var -type f -size +10M    # Files larger than 10MB
```

### `locate` - Fast File Search
```bash
sudo updatedb         # Update index first time
locate config.json
```

---

## 🔗 Command Chaining & Piping

### `;` - Sequential Execution
```bash
mkdir test; cd test
```

### `&&` - Run If Previous Succeeds
```bash
mkdir mydir && cd mydir
```

### `|` - Pipe Output
```bash
ps aux | grep node
cat file.txt | wc -l   # Count lines
```

### `history` - View Command History
```bash
history
```

---

## 🧪 Practice Task

1. Create nested directory:
```bash
mkdir -p ~/linux-practice/logs
```

2. Create log files:
```bash
touch ~/linux-practice/logs/{app.log,error.log,debug.log}
```

3. Add sample content:
```bash
echo "Application started" >> ~/linux-practice/logs/app.log
echo "ERROR: something failed" >> ~/linux-practice/logs/error.log
echo "Debug mode: verbose output" >> ~/linux-practice/logs/debug.log
```

4. View and search content:
```bash
cat ~/linux-practice/logs/error.log
less ~/linux-practice/logs/debug.log
grep -i "error" ~/linux-practice/logs/*.log | wc -l

