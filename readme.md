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

4. created model.py 
    ## make error function
    ``` bash
    ERROR_MSG = 'ERROR'
    # Create a Model to handle the calculator's operation
    def evaluateExpression(expression):
        """Evaluate an expression."""
        try:
            result = str(eval(expression, {}, {})) 
        except Exception:
            result = ERROR_MSG  
    return result
    ```
5. update  main.py with required code
    #### add this to main.py
    ```bash
    model = evaluateExpression
    ```

    6. Make controller.py
    ## Installtion
    ```bash 
    from functools import partial
    ERROR_MSG = 'ERROR'
    ```
    #### make COntroller class with this functions
    ```bash
    class Controller:
    def __init__(self, model, view):
        """Controller initializer."""
        self._evaluate = model
        self._view 	   = view
        # Connect signals and slots
        self._connectSignals()
    def _calculateResult(self):
        """Evaluate expressions."""
        result = self._evaluate(expression=self._view.getDisplayText())
        self._view.setDisplayText(result)
    def _buildExpression(self, sub_exp):
        """Build expression."""
        if self._view.getDisplayText() == ERROR_MSG:
            self._view.clearDisplay()
        expression = self._view.getDisplayText() + sub_exp  
        self._view.setDisplayText(expression)
    def _connectSignals(self):
        """Connect signals and slots."""
        for btnText, btn in self._view.buttons.items():
            if btnText not in {'=', 'C'}:
                btn.clicked.connect(partial(self._buildExpression, btnText))
        self._view.buttons['='].clicked.connect(self._calculateResult)
        self._view.display.returnPressed.connect(self._calculateResult)
        self._view.buttons['C'].clicked.connect(self._view.clearDisplay)
    ```

7. Update main.py
    #### at installtion stage
    ```bash
    from controller import Controller
    ```
    #### at main function stage
    ```bash
    Controller(model=model, view=view)
    ```
8. Update redeme.md file