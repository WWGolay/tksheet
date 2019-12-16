# tksheet [![PyPI version shields.io](https://img.shields.io/pypi/v/tksheet.svg)](https://pypi.python.org/pypi/tksheet/) [![License: MIT](https://img.shields.io/badge/License-MIT%20-blue.svg)](https://github.com/ragardner/tksheet/blob/master/LICENSE.txt) [![GitHub Release Date](https://img.shields.io/github/release-date-pre/ragardner/tksheet.svg)](https://github.com/ragardner/tksheet/releases)

Python 3.6+ tkinter table widget for displaying tabular data

```
pip install tksheet
```

### Features
 - Display and modify tabular data
 - Stores its display data as a Python list of lists, sublists being rows
 - Runs smoothly even with millions of rows/columns
 - Edit cells directly
 - Drag and drop columns and rows
 - Multiple line headers and rows
 - Expand row heights and column widths
 - Change fonts and font size
 - Change any colors in the sheet
 - Left or Centre text alignment
 - Copes with cell elements not being strings
 
### [Version release notes](https://github.com/ragardner/tksheet/blob/master/RELEASE_NOTES.md)

Work on this repository is ongoing, improvements in usability, functionality and finally documentation

Upcoming changes in 4.1.7 - 4.1.8:
 - Changes to multiple_selection mode, renaming it to toggle_selection and reworking it
 - Writing full documentation
Planned future changes:
 - Ctrl + click selection
 - Editing row index/header
 - Display subset of rows
 - More builtin functionality on right click

### Basic Demo:

```python
from tksheet import Sheet
import tkinter as tk


class demo(tk.Tk):
    def __init__(self):
        tk.Tk.__init__(self)
        self.grid_columnconfigure(0, weight = 1)
        self.grid_rowconfigure(0, weight = 1)
        self.sheet_demo = Sheet(self,
                                width = 1000,
                                height = 700,
                                align = "w",
                                header_align = "center",
                                row_index_align = "center",
                                row_index_width = 50,
                                total_rows = 2000,
                                total_columns = 10)
        self.sheet_demo.enable_bindings(("single",
                                         "drag_select",
                                         "column_drag_and_drop",
                                         "row_drag_and_drop",
                                         "column_select",
                                         "row_select",
                                         "column_width_resize",
                                         "double_click_column_resize",
                                         "row_width_resize",
                                         "column_height_resize",
                                         "arrowkeys",
                                         "row_height_resize",
                                         "double_click_row_resize",
                                         "copy",
                                         "cut",
                                         "paste",
                                         "delete",
                                         "undo",
                                         "edit_cell",
                                         "rc_insert_column",
                                         "rc_delete_column",
                                         "rc_insert_row",
                                         "rc_delete_row"))
        self.sheet_demo.grid(row = 0, column = 0, sticky = "nswe")
        

        """_________________________ EXAMPLES _________________________ """
        """_____________________________________________________________"""

        # __________ CHANGING THEME __________

        #self.sheet_demo.change_theme("dark")

        # __________ HIGHLIGHT / DEHIGHLIGHT CELLS __________

        self.sheet_demo.highlight_cells(row = 0, column = 0, bg = "#ed4337", fg = "white")
        self.sheet_demo.highlight_cells(row = 0, bg = "#ed4337", fg = "white", canvas = "row_index")
        self.sheet_demo.highlight_cells(column = 0, bg = "#ed4337", fg = "white", canvas = "header")

        # __________ SETTING OR RESETTING TABLE DATA __________
        
        self.data = [[f"Row {r} Column {c}" for c in range(10)] for r in range(2000)]
        self.sheet_demo.data_reference(self.data)

        # __________ DISPLAY SUBSET OF COLUMNS __________

        #self.sheet_demo.display_subset_of_columns(indexes = [5, 7, 9, 1], enable = True)

        # __________ SETTING HEADERS __________

        #self.headers = [f"Header {c}" for c in range(100)]
        #self.sheet_demo.headers(self.headers)

        # __________ INSERTING A ROW __________

        #self.sheet_demo.insert_row(row = (f"my new row here {c}" for c in range(100)), idx = 0) # a filled row at the start
        #self.sheet_demo.insert_row() # an empty row at the end

        # __________ INSERTING A COLUMN __________

        #self.sheet_demo.insert_column(column = (f"my new col here {r}" for r in range(5000)), idx = 0) # a filled column at the start
        #self.sheet_demo.insert_column() # an empty column at the end

        # __________ HIDING THE ROW INDEX AND HEADERS __________

        #self.sheet_demo.hide("row_index")
        #self.sheet_demo.hide("top_left")
        #self.sheet_demo.hide("header")

        # __________ BINDING A FUNCTION TO USER SELECTS CELL __________

        self.sheet_demo.extra_bindings([
                                        ("cell_select", self.cell_select),
                                        ("shift_cell_select", self.shift_select_cells),
                                        ("drag_select_cells", self.drag_select_cells),
                                        ("ctrl_a", self.ctrl_a),
                                        ("row_select", self.row_select),
                                        ("shift_row_select", self.shift_select_rows),
                                        ("drag_select_rows", self.drag_select_rows),
                                        ("column_select", self.column_select),
                                        ("shift_column_select", self.shift_select_columns),
                                        ("drag_select_columns", self.drag_select_columns),
                                        ]
                                       )
        
    def cell_select(self, response):
        print (response)

    def shift_select_cells(self, response):
        print (response)

    def drag_select_cells(self, response):
        pass
        #print (response)

    def ctrl_a(self, response):
        print (response)

    def row_select(self, response):
        print (response)

    def shift_select_rows(self, response):
        print (response)

    def drag_select_rows(self, response):
        pass
        #print (response)
        
    def column_select(self, response):
        print (response)

    def shift_select_columns(self, response):
        print (response)

    def drag_select_columns(self, response):
        pass
        #print (response)
        
app = demo()
app.mainloop()


```

----

### Light Theme

![alt text](https://i.imgur.com/yoa6K6T.jpg)


### Dark Theme

![alt text](https://i.imgur.com/JrZD5Lf.jpg)

----

