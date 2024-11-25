# Phishing Link Scanner

## Installation 

### Steps to Save Your Script Using Nano

1. **Open Terminal**:
   - Launch your terminal application.

2. **Create a New File with Nano**:
   - To create a new file named `phishing_link_scanner`, type:
     ```bash
     nano phishing_link_scanner
     ```

3. **Paste Your Code into Nano**:
   - After opening the `nano` editor, paste the phishing_link_scanner code into the editor. To paste in a terminal, you can usually use `Ctrl + Shift + V` (on Linux) or `Command + V` (on macOS).

   Here’s the code to paste:

       
       python
       import requests  
       from bs4 import BeautifulSoup  

       def scan_phishing_link(url):  
       """  
       Scans a given URL for phishing indicators.  

       Args:  
        url (str): The URL to scan.  

       Returns:  
        bool: True if the URL is likely a phishing link, False otherwise.  
        """  

       try:  
        response = requests.get(url, timeout=5)  
        soup = BeautifulSoup(response.content, 'html.parser')  

        # Check for common phishing indicators  
        if "https" not in url:  
            return True  

        # Check for suspicious domains  
        if "login" in url or "account" in url or "verify" in url or "paypal" in url or "amazon" in url:  
            return True  

        # Check for unusual website structure  
        if len(soup.find_all("a")) < 5:  
            return True  

        # Check for suspicious content  
        if "password" in soup.text.lower() or "credit card" in soup.text.lower():  
            return True  

        # Check for suspicious code (e.g., JavaScript that redirects to a different page)  
        if "<script>" in soup.text:  
            return True  

        # No suspicious indicators found  
        return False  

       except requests.exceptions.Timeout:  
        print("Request timed out.")  
        return True  

       except requests.exceptions.RequestException as e:  
        print(f"Error: {e}")  
        return True  

       if __name__ == "__main__":  
       while True:  
        url = input("Enter the URL to scan (or 'exit' to quit): ")  
        if url == "exit":  
            break  

        if scan_phishing_link(url):  
            print("Warning: This link may be a phishing attempt.")  
        else:  
            print("This link appears to be safe.")  
       ```

4. **Save the File**:
   - After pasting the code, save the file by pressing `Ctrl + O` (the letter O, not zero).
   - Nano will prompt you to confirm the file name. Just press `Enter` to confirm.

5. **Exit Nano**:
   - To exit the nano editor, press `Ctrl + X`.

### 4: Run Your Script

1. **Make Sure You’re in the Right Directory**:
   - Verify that you're still in the directory where you saved the file.

2. **Run the Script**:
   - Execute the script with the following command:
```bash
python3 phishing_link_scanner
```
or
```bash
python phishing_link_scanner.py
```


3. **Test the Functionality**:
   
   -Enter various URLs when prompted to see if they are flagged as phishing attempts.


### Optional: Check if Python is Installed

If you encounter issues running the script, ensure that Python is installed on your system. You can check this by typing:

```bash
python --version
```
or
```bash
python3 --version
```

If Python is not installed, you must download and install it from [python. org](https://www.python.org/downloads/).

