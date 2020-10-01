1. run test.py
2. created view.py
    ## Installation
    ```bash
    from PyQt5.QtCore import Qt
    from PyQt5.QtWidgets import QMainWindow
    from PyQt5.QtWidgets import QWidget
    from PyQt5.QtWidgets import QGridLayout
    from PyQt5.QtWidgets import QLineEdit
    from PyQt5.QtWidgets import QPushButton
    from PyQt5.QtWidgets import QVBoxLayout
    ```
    #### make function
    ```bash
    def setDisplayText(self, text):
        """Set display's text."""
        self.display.setText(text)
        self.display.setFocus()
    def getDisplayText(self):
        """Get display's text."""
        return self.display.text()
    
    def clearDisplay(self):
        """Clear the display."""
        self.setDisplayText('')
    ``` 
