# create a panel 

```python 
from rich.panel import Panel
from rich import print

app: str = ' Codezilla '
text: str = " This is a simple text "
print(Panel(text, title=app))
```


# Create a table in rich 

```python 
from rich.table import Table, Column 

# instanciate the table object 
table = Table(title="Tasks")
# create table columns 
table.add_column(" # ID ", style="cyan", no_wrap="True")
table.add_column(" Title ", style="cyan")
table.add_column(" Done ", style="cyam")
table.add_column(" Description ", style="cyan")
table.add_column(" Status ", style="green")

# add rows 
table.add_row(data1, data2, data3, data4, data5)
```


# Get a yes / No answer from the user 

```python 
from rich.prompt import Prompt, Confirm
confirm: bool = Confirm.ask("[yellow]-> Are you sure you want to delete this task ")
```