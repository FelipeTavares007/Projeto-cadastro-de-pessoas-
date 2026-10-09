# Projeto-cadastro-de-pessoas-

import tkinter as tk
from tkinter import messagebox
import re

clientes = [] 
PADRAO_EMAIL = re.compile(r"^[\w.+-]+@[\w-]+(\.[\w-]+)+$")

def cadastro_cliente():
    nome_digitado = entry_nome.get().strip()
    telefone_digitado = entry_telefone.get().strip()
    email_digitado = entry_email.get().strip()

    if not nome_digitado or not telefone_digitado or not email_digitado:
        messagebox.showwarning("Atenção", "Preencha todos os campos para continuar!")
        return

    if len(nome_digitado) < 2:
        messagebox.showwarning("Atenção", "Informe um nome com pelo menos 2 caracteres.")
        return

    digitos = re.sub(r"\D", "", telefone_digitado)
    if len(digitos) not in (10, 11):
        messagebox.showwarning("Atenção", "O telefone deve ter 10 ou 11 dígitos (com DDD).")
        return

    if not PADRAO_EMAIL.match(email_digitado):
        messagebox.showwarning("Atenção", "Informe um e-mail válido (ex.: nome@dominio.com).")
        return

    for cliente in clientes:
        if nome_digitado.lower() == cliente["nome"].lower():
            messagebox.showwarning("Atenção", "Este nome já foi cadastrado, tente novamente.")
            return
         
    clientes.append({
        "nome": nome_digitado,
        "telefone": telefone_digitado,
        "email": email_digitado
    })

    msg = f"Dados cadastrados com sucesso:\n\nNome: {nome_digitado}\nTelefone: {telefone_digitado}\nEmail: {email_digitado}"
    messagebox.showinfo("Sucesso", msg)

    entry_nome.delete(0, tk.END)            
    entry_telefone.delete(0, tk.END)
    entry_email.delete(0, tk.END)


def lista_clientes():
    janela3 = tk.Tk()
    janela3.title("Clientes")
    janela3.geometry("500x400")

    canvas = tk.Canvas(janela3)
    canvas.pack(side="left", fill="both", expand=True)
    barra = tk.Scrollbar(janela3, orient="vertical", command=canvas.yview)
    barra.pack(side="right", fill="y")
    canvas.configure(yscrollcommand=barra.set)

    frame_clientes = tk.Frame(canvas)

    canvas.create_window((0, 0), window=frame_clientes, anchor="nw")
    frame_clientes.bind("<Configure>", lambda e: canvas.configure(scrollregion=canvas.bbox("all")))

    for cliente in clientes:
        frame_cliente = tk.Frame(frame_clientes, bd=2, relief="groove")
        frame_cliente.pack(fill="x", padx=20, pady=20)
        
        lbl_cliente = tk.Label(frame_cliente, text="Nome: " + cliente["nome"])
        lbl_cliente.pack(pady=2, anchor="w")

        lbl_telefone = tk.Label(frame_cliente, text="Telefone: " + cliente["telefone"])
        lbl_telefone.pack(pady=2, anchor="w")

        lbl_email = tk.Label(frame_cliente, text="Email: " + cliente["email"])
        lbl_email.pack(pady=2, anchor="w")


def procurar_clientes():
    janela.destroy()

    janela2 = tk.Tk()
    janela2.title("Lista de Clientes")
    janela2.geometry("400x200")

    lbl_nome = tk.Label(janela2, text="Nome")
    lbl_nome.grid(row=0, column=0, padx=10, pady=10)
    entry_nome2 = tk.Entry(janela2, width=30)
    entry_nome2.grid(row=0, column=1, padx=10, pady=10)

    btn_buscar = tk.Button(janela2, text="Buscar Clientes", bg="#2B9230", fg="white", command=lambda: buscar_cliente(entry_nome2))
    btn_buscar.grid(row=3, column=0, columnspan=2, pady=15)


def buscar_cliente(campo):
    termo = campo.get().strip()
    encontrados = []

    for cliente in clientes:
        if termo.lower() in cliente["nome"].lower():
            encontrados.append(cliente)

    if encontrados:
        texto_resultado = ""
        for c in encontrados:
            texto_resultado += f"Nome: {c['nome']} | Tel: {c['telefone']} | Email: {c['email']}\n"
        messagebox.showinfo("Resultado", texto_resultado)
    else:
        messagebox.showinfo("Resultado", "Nenhum cliente encontrado.")


janela = tk.Tk()
janela.title("Tela Inicial de Cadastro de Clientes")
janela.geometry("400x250")

lbl_nome = tk.Label(janela, text="Nome")
lbl_nome.grid(row=0, column=0, padx=10, pady=10)
entry_nome = tk.Entry(janela, width=30) 
entry_nome.grid(row=0, column=1, padx=10, pady=10)

lbl_telefone = tk.Label(janela, text="Telefone:")
lbl_telefone.grid(row=1, column=0, padx=10, pady=10)
entry_telefone = tk.Entry(janela, width=30)
entry_telefone.grid(row=1, column=1, padx=10, pady=10)

lbl_email = tk.Label(janela, text="Email:")
lbl_email.grid(row=2, column=0, padx=10, pady=10)
entry_email = tk.Entry(janela, width=30)
entry_email.grid(row=2, column=1, padx=10, pady=10)

btn_salvar = tk.Button(janela, text="Adicionar Cliente", bg="#2196F3", fg="white", command=cadastro_cliente)
btn_salvar.grid(row=3, column=0, columnspan=2, pady=15)

btn_consulta = tk.Button(janela, text="Lista de Clientes", bg="#0F7E39", fg="white", command=lista_clientes)
btn_consulta.grid(row=3, column=2, columnspan=2, pady=15)

btn_procura = tk.Button(janela, text="Procurar Clientes", bg="#FFFB04", fg="black", command=procurar_clientes)
btn_procura.grid(row=4, column=0, columnspan=2, pady=15)

janela.mainloop()
