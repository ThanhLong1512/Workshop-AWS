---
title: "Instructions for cloning the FE&BE project and uploading it to Github Repository"
date: "2025-06-21"
weight: 3
chapter: false
pre: " <b> 3.1.3 </b> "
---

After creating your two repositories on GitHub, you'll need to download [Visual Studio Code](https://code.visualstudio.com/) và [GitHub Desktop](https://desktop.github.com/download/)
These tools will help streamline cloning and pushing projects to GitHub

1. **What is Visual Studio Code**
   ![VSCODE](/images/3.Containerization/3.1/3.1.3/2.png)

**Visual Studio Code (VS Code)** is a free, cross-platform source code editor developed by Microsoft. It has quickly become one of the most popular editors among developers due to its user-friendly interface, powerful features, and extensibility.

**Why Choose VS Code?**

- Free & Open-Source – Licensed under MIT, allowing free use, modification, and contributions
- Cross-Platform – Works on Windows, macOS, and Linux.
- User-Friendly – Simple, intuitive interface for beginners and experts.
- Multi-Language Support – Supports JavaScript, Python, Java, C++, C#, Go, PHP, and more with IntelliSense (smart code suggestions), debugging, and syntax highlighting.

2. **What is GitHub Desktop ?**

   ![GitHub Desktop](/images/3.Containerization/3.1/3.1.3/1.png)

   **GitHub Desktop** is a GUI tool that simplifies Git workflows (cloning, committing, pushing) without using the command line.

   **Pros & Cons**

   - **Pros:**

     - Easy-to-use interface for managing repositories.
     - Seamless GitHub integration (pull requests, code reviews).
     - Auto-updates for security & features.

   - **Cons:**

     - No official Linux support.
     - Limited advanced Git features (e.g., interactive rebase).
     - Optimized for GitHub (less support for other Git platforms).

### Steps to Clone FE/BE Projects & Push to GitHub

1. **Step 1:** Access the FE & BE template repositories: [FE Repository](https://github.com/ThanhLong1512/FE-Dentist) and [BE repository](https://github.com/ThanhLong1512/BE-Dentist).
2. **Step 2:**Copy the BE repository URL, then open **GitHub Desktop**
   ![GitHub Desktop](/images/3.Containerization/3.1/3.1.3/3.png)
3. **Step 3:** In GitHub Desktop, go to: **File -> Clone a repository -> URL**.
   ![GitHub Desktop](/images/3.Containerization/3.1/3.1.3/4.png)
4. **Step 4:** Paste the repository URL and choose a local folder to save it.
   ![GitHub Desktop](/images/3.Containerization/3.1/3.1.3/5.png)
5. **Step 5:** After cloning, open VS Code.
6. **Step 6:** Select **File -> Open folder to start working -> Select the cloned project folder**.
   ![GitHub Desktop](/images/3.Containerization/3.1/3.1.3/6.png)
7. **Step 7:** Open a terminal **Terminal -> New Terminal** and run: **npm install**.
   ![GitHub Desktop](/images/3.Containerization/3.1/3.1.3/7.png)
8. **Step 8:** Run the project:
   ![GitHub Desktop](/images/3.Containerization/3.1/3.1.3/8.png)
9. **Step 9:** Push the project to your own repository (AWS-BE)
10. **Step 10:** Remove the old remote: **git remote remove origin**
11. **Step 11:** Copy your **AWS-BE** repository URL from GitHub:
    ![GitHub Desktop](/images/3.Containerization/3.1/3.1.3/9.png)
12. **Step 12:** Add your new remote and push: **git push -u origin main**.
    ![GitHub Desktop](/images/3.Containerization/3.1/3.1.3/10.png)
13. **Step 13:** Repeat Steps 2-12 for the FE project.
