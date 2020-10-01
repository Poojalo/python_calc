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
3. created main.py for testng view
     ## Installation
    ```bash
    import sys
    from PyQt5.QtWidgets import QApplication
    from view import GUI
    #from controller import Controller
    #from  model import evaluateExpression
    ```
    #### define main function  
    ```bash
    def main():
    """Main function."""
    # Create an instance of QApplication
    pycalc = QApplication(sys.argv)
    # Show the calculator's GUI
    view = GUI()
    view.show()
    #model = evaluateExpression
    #Controller(model=model, view=view)
    sys.exit(pycalc.exec_())
    if __name__ == "__main__":
        main()  
    ```