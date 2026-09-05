from kivy.app import App
from kivy.uix.boxlayout import BoxLayout
from kivy.uix.gridlayout import GridLayout
from kivy.uix.button import Button
from kivy.uix.textinput import TextInput
from kivy.core.window import Window

Window.clearcolor = (0.95, 0.95, 0.95, 1)


class Calculator(App):

    def build(self):
        root = BoxLayout(
            orientation="vertical",
            padding=10,
            spacing=10
        )

        self.display = TextInput(
            text="0",
            readonly=True,
            halign="right",
            font_size=38,
            background_color=(1, 1, 1, 1),
            foreground_color=(0.05, 0.05, 0.05, 1),
            size_hint_y=0.25
        )
        root.add_widget(self.display)

        buttons = [
            ["C", "⌫", "%", "÷"],
            ["7", "8", "9", "×"],
            ["4", "5", "6", "−"],
            ["1", "2", "3", "+"],
            ["0", ".", "=", ""]
        ]

        grid = GridLayout(
            cols=4,
            spacing=8
        )

        for row in buttons:
            for text in row:
                if text == "":
                    grid.add_widget(BoxLayout())
                    continue

                button = Button(
                    text=text,
                    font_size=28,
                    background_normal="",
                    background_color=(1, 1, 1, 1),
                    color=(0.05, 0.05, 0.05, 1)
                )

                button.bind(on_press=self.press)
                grid.add_widget(button)

        root.add_widget(grid)
        return root

    def press(self, button):
        value = button.text

        if value == "C":
            self.display.text = "0"

        elif value == "⌫":
            self.display.text = self.display.text[:-1]
            if not self.display.text:
                self.display.text = "0"

        elif value == "=":
            try:
                expression = self.display.text
                expression = expression.replace("×", "*")
                expression = expression.replace("÷", "/")
                expression = expression.replace("−", "-")

                result = eval(expression, {"__builtins__": None}, {})
                self.display.text = str(result)

            except:
                self.display.text = "Error"

        else:
            if self.display.text == "0" or self.display.text == "Error":
                self.display.text = value
            else:
                self.display.text += value


if __name__ == "__main__":
    Calculator().run()