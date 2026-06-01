
import tkinter as tk
from tkinter import ttk

MULTIPLIER = 9.5

class ConverterApp:
    def __init__(self, root):
        self.root = root
        root.title("CGPA / SGPA Converter")
        root.geometry("500x350")
        root.resizable(False, False)

        self.hue = 0

        self.main = tk.Frame(root, padx=20, pady=20)
        self.main.pack(expand=True, fill="both")

        self.title = tk.Label(
            self.main,
            text="CGPA / SGPA ➜ Percentage",
            font=("Segoe UI", 20, "bold")
        )
        self.title.pack(pady=10)

        self.subtitle = tk.Label(
            self.main,
            text="Enter your CGPA or SGPA",
            font=("Segoe UI", 10)
        )
        self.subtitle.pack()

        self.entry = ttk.Entry(self.main, font=("Segoe UI", 16), justify="center")
        self.entry.pack(pady=20, ipadx=30, ipady=8)

        self.btn = ttk.Button(self.main, text="Convert", command=self.convert)
        self.btn.pack(pady=10)

        self.result = tk.Label(
            self.main,
            text="Percentage: --",
            font=("Segoe UI", 18, "bold")
        )
        self.result.pack(pady=20)

        self.footer = tk.Label(
            self.main,
            text="Formula: Percentage = GPA × 9.5",
            font=("Segoe UI", 9)
        )
        self.footer.pack(side="bottom", pady=10)

        self.animate_bg()

    def convert(self):
        try:
            gpa = float(self.entry.get())
            percentage = gpa * MULTIPLIER
            self.animate_result(f"Percentage: {percentage:.2f}%")
        except ValueError:
            self.animate_result("Enter a valid number")

    def animate_result(self, text):
        self.result.config(text=text)
        self.pulse(0)

    def pulse(self, step):
        sizes = [18, 20, 22, 24, 22, 20, 18]
        if step < len(sizes):
            self.result.config(font=("Segoe UI", sizes[step], "bold"))
            self.root.after(40, lambda: self.pulse(step + 1))

    def animate_bg(self):
        r = int(127 + 127 * __import__("math").sin(self.hue * 0.03))
        g = int(127 + 127 * __import__("math").sin(self.hue * 0.03 + 2))
        b = int(127 + 127 * __import__("math").sin(self.hue * 0.03 + 4))

        color = f"#{r:02x}{g:02x}{b:02x}"

        self.root.configure(bg=color)
        self.main.configure(bg=color)

        for widget in [self.title, self.subtitle, self.result, self.footer]:
            widget.configure(bg=color)

        self.hue += 1
        self.root.after(50, self.animate_bg)

root = tk.Tk()
style = ttk.Style()
style.theme_use("clam")

app = ConverterApp(root)
root.mainloop()
