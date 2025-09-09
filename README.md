
# Parallel Encryption and Decryption (Windows Compatible)

## Overview

This project provides a parallelized solution for encrypting and decrypting files in a directory using C++. It leverages process management, shared memory, and semaphores to efficiently handle multiple files concurrently. The codebase is now refactored for Windows compatibility, using the Windows API for all parallel and shared memory operations.

## Features

- **Parallel Processing:** Uses Windows processes to handle multiple encryption/decryption tasks in parallel.
- **Shared Memory:** Implements a shared queue for task management using Windows file mapping.
- **Semaphores:** Synchronizes access to the shared queue with Windows semaphores.
- **Flexible Task Management:** Automatically scans a directory and submits each file as a task for encryption or decryption.
- **Python Integration:** Includes a Python script (`makeDirs.py`) to set up test directories and files.

## Getting Started

### 1. Clone the repository
```bash
git clone <repo-url>
cd encrypty-add-sharedMemory
```

### 2. Set up test directories (optional)
```bash
python -m venv myvenv
myvenv\Scripts\activate  # On Windows
python makeDirs.py
```

### 3. Build the project (Windows)
```powershell
mingw32-make  # or make if using MSVC
```

### 4. Run the main program
```powershell
./encrypt_decrypt.exe
```
Follow the prompts:
- Enter the directory name created by `makeDirs.py` (e.g., `test`)
- Enter `encrypt` or `decrypt` to choose the action

## File Structure

- `main.cpp` — Main entry point, handles user input and task submission.
- `src/app/processes/ProcessManagement.*` — Manages process creation, shared memory, and semaphores.
- `src/app/processes/Task.hpp` — Defines the task structure for file operations.
- `src/app/encryptDecrypt/CryptionMain.cpp` — Child process entry point for encryption/decryption.
- `src/app/encryptDecrypt/Cryption.*` — Implements the encryption/decryption logic.
- `src/app/fileHandling/IO.*` — File I/O utilities.
- `src/app/fileHandling/ReadEnv.cpp` — Reads the encryption key from `.env`.
- `makeDirs.py` — Python script to create test directories/files.
- `Makefile` — Build instructions for Windows (MinGW-w64 or MSVC).
- `.gitignore` — Excludes build artifacts, environment files, and user-specific files.
- `README.md` — Project documentation.

## Notes

- The project is now Windows-compatible. All Linux-specific code has been refactored to use the Windows API.
- Do **not** commit build artifacts (`.exe`, `.o`, etc.) or your `.env` file. Use the provided `.gitignore`.
- For Linux support, use the original branches or refactor as needed.

## Example .gitignore
See the included `.gitignore` file for recommended exclusions.

