How to create own PyQt5 QWidget

```python
from PyQt5.QtWidgets import QWidget, QPushButton
from PyQt5.QtCore import QRect, pyqtSlot
# two lines

class CustomWidget(QWidget):
    def __init__(self):
        super(CustomWidget, self).__init__()
        
        # init all object variables
        self.button_geometry = QRect("""some size""")  # <name of subwidget>_<name of variable>
        self.initUI()
    # one line
    def initUI(self):
        """
        Тут создаются все внутренние под-виджеты
        """
        self.button = QPushButton("button", self)  # all sub widget MUST have parent - self, name MUST be with camel case
        self.button.setGeometry(self.button_geometry)
        self.button.clicked.connect(self.onClickButton)  # all slots MUST have name on<Event name><SubwidgetName>
    
    @pyqtSlot()  # MUST mark, it is slot
    def onClickButton(self):
        pass
```
