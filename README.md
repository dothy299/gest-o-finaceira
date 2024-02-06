import tkinter as tk

class GestaoFinanceiraApp:
    def __init__(self, master):
        self.master = master
        self.master.title("Gestão Financeira")

        self.saldo = 0

        self.lbl_saldo = tk.Label(master, text="Saldo: R$ {}".format(self.saldo))
        self.lbl_saldo.pack()

        self.lbl_transacao = tk.Label(master, text="Nova Transação:")
        self.lbl_transacao.pack()

        self.entry_transacao = tk.Entry(master)
        self.entry_transacao.pack()

        self.btn_adicionar = tk.Button(master, text="Adicionar Transação", command=self.adicionar_transacao)
        self.btn_adicionar.pack()

        self.lbl_msg = tk.Label(master, text="")
        self.lbl_msg.pack()

    def adicionar_transacao(self):
        try:
            valor = float(self.entry_transacao.get())
            self.saldo += valor
            self.lbl_saldo.config(text="Saldo: R$ {}".format(self.saldo))
            self.lbl_msg.config(text="Transação adicionada com sucesso!", fg="green")
        except ValueError:
            self.lbl_msg.config(text="Por favor, insira um valor válido.", fg="red")

def main():
    root = tk.Tk()
    app = GestaoFinanceiraApp(root)
    root.mainloop()

if __name__ == "__main__":
    main()
