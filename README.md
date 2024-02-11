# Story_Maker
```python
import g4f
import customtkinter as ctk


#main window
ctk.set_appearance_mode("Dark")
root = ctk.CTk()
root.geometry("1000x700+350+50")
root.title("Story Maker")
root.resizable(False, False)

#output slider's value
def SLIDER(value):
    val = int(value)
    words.configure(text = (f"{val}"))

#output of story
def MAKE():
    textbox.configure(state = "normal")
    textbox.delete("1.0", ctk.END)
    val = int(slide.get())
    theme1 = ent1.get()
    theme2 = ent2.get()
    theme3 = ent3.get()

    #respose for AI
    response = g4f.ChatCompletion.create(
        model = g4f.models.default,
        messages= [{"role":"user", "content":f"DO NOT WRITE ANY SMILES OR *!!!Write a COMPLETED story by THE themes: {theme1}, {theme2}, {theme3}. ON {val} WORDS. DO NOT WRITE ANY EXTRA INFORMATION! WRITE ONLY STORY WITHOUT SMILES, SPECIAL SYMBOLS AND ETC!!!"}],
        stream = True,)
    #output in textbox
    for message in response:
        textbox.insert(ctk.END, message)
    textbox.configure(state = "disabled")


#main interface
ctk.CTkLabel(master = root, text = "Story Maker!", font =("Lucida Console", 30)).place( relx = 0.5, rely = 0.05,anchor = ctk.CENTER)
ctk.CTkLabel(master = root, text = "Themes:", font =("Lucida Console", 24)).place( relx = 0.05, rely = 0.25,anchor = ctk.W)
ctk.CTkLabel(master = root, text = "Length:",  font =("Lucida Console", 24)).place( relx = 0.05, rely = 0.15,anchor = ctk.W)
btn = ctk.CTkButton(master=root, text="Create!", font =("Lucida Console", 20), command=MAKE)
btn.place(relx = 0.5, rely = 0.95, anchor = ctk.CENTER)


textbox= ctk.CTkTextbox(master=root, width=900, height=410, fg_color="#3c3d3d", font =("Lucida Console", 16), border_width=2,border_color=("#565b5e"), state = "disabled")
textbox.place(relx = 0.50, rely = 0.6,anchor = ctk.CENTER)

slide = ctk.CTkSlider(master = root, from_= 50, to = 300, width= 550, number_of_steps=25, command=SLIDER)
slide.place(relx = 0.17, rely = 0.15,anchor = ctk.W)
slide.set(30)
value = slide.get()

ctk.CTkLabel(master = root, text = "words", font =("Lucida Console",20)).place( relx = 0.88, rely = 0.15,anchor = ctk.CENTER)
ctk.CTkLabel(master = root, text = "About", font =("Lucida Console",20)).place( relx = 0.76, rely = 0.15,anchor = ctk.CENTER)
words = ctk.CTkLabel(master = root, text = "50", font =("Lucida Console",20))
words.place(relx = 0.82, rely = 0.15,anchor = ctk.CENTER)

ent1 = ctk.CTkEntry(master = root,font =("Lucida Console", 16), width = 230)
ent1.place(relx = 0.175, rely = 0.25,anchor = ctk.W)
ent2 = ctk.CTkEntry(master = root,font =("Lucida Console", 16), width = 230)
ent2.place(relx = 0.445, rely = 0.25,anchor = ctk.W)
ent3 = ctk.CTkEntry(master = root,font =("Lucida Console", 16), width = 230)
ent3.place(relx = 0.715, rely = 0.25,anchor = ctk.W)


root.mainloop()
```

"Story Maker" project is a simple application for creating stories based on given themes and text length.

## Installation
Clone the repository to your computer:
```bush
git clone https://github.com/KAMAbee/Story_Maker.git
```

Install the necessary dependencies:
```terminal
pip install -r requirements.txt
 ```
  
## Running:
To run the application, execute the following command in the terminal:
```terminal
python main.py
 ```

## Usage 
- Select the desired length of the story using the slider.
- Enter themes for the story in the respective text fields.
- Click the "Create!" button to get a ready-made story.

## Technologies
- Python 3
- CustomTkinter
- GPT-4

## Contributing
If you have any suggestions for improving the project or find any bugs, you can contribute to the project by creating a pull request.
Any ideas or additions are welcome!
