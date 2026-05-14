# Haelicx

Haelicx is a collection of GitHub Actions workflows that enable you to download files from arbitrary URLs, organize them, clean the downloads directory, and even browse websites capturing screenshots and media. The project is designed to be easy to use, fully automated, and integrates seamlessly with your GitHub repository.

## Workflows

| Workflow | Description | Trigger |
|---|---|---|
| 📥 Haelicx 01-Download from URL | Download one or more files from URLs, optionally create a split ZIP archive, and push the result to the repository. | Manual (`workflow_dispatch`) – Provide a space‑separated list of URLs, choose `normal` or `zip` mode, and optionally set a password for ZIP archives. |
| 📂 Haelicx Sort files | Organize split ZIP, DEB, or part files into sub‑folders based on their base name. | Manual (`workflow_dispatch`) |
| 🗑 Haelicx Clean downloads folder | Remove all files from the `downloads/` folder and recreate it with a default `README.md`. | Manual (`workflow_dispatch`) – Requires confirmation due to the destructive nature. |
| 🌐 Haelicx Browse the Web | Visit a website, download all media assets, capture a screenshot, and store everything in a structured folder under `pages/`. | Manual (`workflow_dispatch`) – Provide the URL of the page to visit. |

## Usage

### 1. Download Files

1. Open the **Download** workflow in the Actions tab.  
2. Click **Run workflow**.  
3. In the **URLs** field, enter space‑separated URLs (e.g., `https://example.com/file1.zip https://example.com/file2.mp4`).  
4. Choose **Mode** (`normal` to keep files as‑is or `zip` to create a split ZIP archive).  
5. (Optional) Enter a password if you selected `zip` mode.  
6. Click **Run workflow**.

The workflow will:
- Download each file, retrying on failure.  
- Split large files into 45 MB chunks for GitHub.  
- Push the files to your repository and create a `README.md` with download links.  

### 2. Organize Split Files

If you have many split parts (e.g., `file.z01`, `file.z02`), run the **Sort** workflow. It will:
- Create a folder named after the base file.  
- Move all related parts into that folder.  

### 3. Clean Downloads

When you want to clear the `downloads/` folder, run the **Clean** workflow. The workflow:
- Deletes all tracked files in `downloads/`.  
- Recreates the folder with a default `README.md`.  

**Caution:** This operation is destructive. Only run it if you are sure you want to delete all downloaded content.

### 4. Browse a Website

1. Run the **Browse** workflow.  
2. Enter the URL of the website you want to capture.  
3. The workflow will:
   - Download the page’s HTML.  
   - Capture a full‑page screenshot.  
   - Extract all media assets (`.png`, `.jpg`, `.mp4`, etc.).  
   - Store everything under `pages/<domain>/<slug>/<timestamp>/`.  
   - Create an `index.md` with links to all files and a screenshot.  

The `browse.md` file maintains a list of all captured pages for quick navigation.

## Repository Structure

downloads/ ├─ / │ ├─ <file1.zip> │ ├─ README.md ├─ / │ ├─ <file2.z01> │ ├─ <file2.z02> │ ├─ README.md pages/ ├─ /// │ ├─ page.html │ ├─ screenshot.png │ ├─ media/ │ │ ├─ image1.png │ │ ├─ video1.mp4 │ ├─ index.md browse.md README.md


## Contact & Support

- **Telegram:** @haelicx  
- **Source:** This project is open‑source and hosted on GitHub. Feel free to open issues or pull requests.

## License

MIT

*Made by Haelicx*
