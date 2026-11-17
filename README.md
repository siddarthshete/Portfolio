# Personal Portfolio Website

This repository contains my personal portfolio website, created to showcase my skills, projects, resume, and contact details. The portfolio is designed to be simple, responsive, and easy to navigate, with an integrated Excel/Google Sheets workflow for contact submissions.

---

## 🚀 Features

- Clean and responsive portfolio design
- About, skills, projects, and contact sections
- **Excel Workflow Integration:** Contact form submissions are automatically saved to a Google Sheet/Excel file with date and time.
- Resume download support
- Dark mode support
- Organized assets for images and documents

---

## 🛠️ Tech Stack

### Frontend
- HTML5
- CSS3
- JavaScript
- Font Awesome (Icons)

### Workflow Integration
- SheetDB / Google Sheets API (for data persistence)

### Tools
- Git
- GitHub

---

## 📂 Project Structure

```text
portfolio/
├── index.html                     # Main portfolio page
├── style.css                      # Global styles
├── CONTACT_FORM_SETUP.md          # Contact form setup instructions
├── siddarth_photo.png             # Profile photo
├── Resume_Siddarth_Shete.pdf      # Resume PDF
└── README.md                      # Project documentation
```

---

## 🌐 Live Demo

If GitHub Pages is enabled, the site will be available at:
`https://siddarthshete.github.io/portfolio/`

---

## ⚙️ How to Run Locally

1. **Clone the repository:**
   ```bash
   git clone https://github.com/siddarthshete/portfolio.git
   ```

2. **Navigate to the project folder:**
   ```bash
   cd portfolio
   ```

3. **Open the portfolio:**
   Open `index.html` directly in your browser or use "Live Server" in VS Code.

---

## 📬 Contact Form Setup

This project uses a serverless workflow to store contact form submissions in a spreadsheet.

1. Create a Google Sheet with headers: `name`, `email`, `subject`, `message`, `date`, `time`, `timestamp`.
2. Use [SheetDB](https://sheetdb.io/) to create an API for your sheet.
3. Update the `SHEETDB_API_URL` in `index.html`.

For detailed instructions, see: **[CONTACT_FORM_SETUP.md](CONTACT_FORM_SETUP.md)**

---

## 👤 Author

**Siddarth Shete**  
Computer Engineering Student

---

## 📄 License

This project is open-source and intended for educational and personal use.
