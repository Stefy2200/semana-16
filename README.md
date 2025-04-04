# semana-16
@@ -0,0 +1,47 @@
 import tkinter as tk
 from tkinter import messagebox
 
 def on_button_click():
     entered_text = text_entry.get()  # Obtiene el texto del Entry
     # Muestra el texto en un Label
     display_label.config(text=entered_text)
     # Muestra el texto en la línea de comandos (CLI)
     print(entered_text)
     # Muestra el texto en una ventana de mensaje (messagebox)
     messagebox.showinfo("Información Ingresada", entered_text)
 
 def on_enter_key(event):
     on_button_click()
 
 def on_escape_key(event):
     root.quit()
 
 root = tk.Tk()
 root.title("Interfaz de Usuario de Demostración")
 root.geometry("400x200")  # Establece un tamaño para la ventana
 
 # Crea un Label para indicar al usuario que ingrese texto
 instruction_label = tk.Label(root, text="Por favor, ingresa un texto:", font=("Arial", 14))
 instruction_label.pack(pady=(10,0))
 
 # Crea un Entry para la entrada de texto
 text_entry = tk.Entry(root, font=("Arial", 14))
 text_entry.pack(pady=10)
 
 # Crea un Button que llamará a la función on_button_click cuando sea clickeado
 button = tk.Button(root, text="Haz clic en mí", command=on_button_click)
 button.pack(pady=(0,10))
 
 # Crea un Label para mostrar el texto ingresado
 display_label = tk.Label(root, font=("Arial", 14))
 display_label.pack(pady=10)
 
 # Vincula la tecla Enter con la función on_enter_key
 root.bind('<Return>', on_enter_key)
 # Vincula la tecla Escape con la función on_escape_key
 root.bind('<Escape>', on_escape_key)
 
 # Pone el foco en la entrada de texto para que el usuario pueda comenzar a escribir inmediatamente
 text_entry.focus_set()
 
 root.mainloop()
 @@ -0,0 +1,47 @@
 import tkinter as tk
 
 def on_left_click(event):
     instructions.config(text="Clic izquierdo detectado.")
 
 def on_right_click(event):
     instructions.config(text="Clic derecho detectado.")
 
 def on_middle_click(event):
     instructions.config(text="Clic de scroll detectado.")
 
 def on_mouse_enter(event):
     event.widget.config(bg='lightblue')
 
 def on_mouse_leave(event):
     event.widget.config(bg='SystemButtonFace')
 
 def on_mouse_move(event):
     position_label.config(text=f"Posición del mouse: x={event.x}, y={event.y}")
 
 root = tk.Tk()
 root.title("Monitor de Eventos de Teclado y Mouse")
 root.geometry("500x400")
 
 instructions = tk.Label(root, text="Instrucciones:\n"
                                    "Clic izquierdo: Detecta clic izquierdo del mouse.\n"
                                    "Clic derecho: Detecta clic derecho del mouse.\n"
                                    "Clic de scroll: Detecta clic con la rueda del mouse.\n"
                                    "Mueve el mouse sobre este texto para ver su posición.",
                         justify=tk.LEFT)
 instructions.pack(pady=10)
 
 # Vinculación de eventos de clic del mouse
 instructions.bind("<Button-1>", on_left_click)
 instructions.bind("<Button-2>", on_middle_click)
 instructions.bind("<Button-3>", on_right_click)
 
 # Vinculación de eventos de movimiento del mouse
 instructions.bind("<Enter>", on_mouse_enter)
 instructions.bind("<Leave>", on_mouse_leave)
 root.bind("<Motion>", on_mouse_move)
 
 # Label para mostrar la posición del mouse
 position_label = tk.Label(root, text="Posición del mouse: x=0, y=0")
 position_label.pack(pady=10)
 
 root.mainloop()
 
