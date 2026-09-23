# projeto-de-gestao-de-sorteio-


👤 Pessoa 1 — Cadastro e estrutura dos sorteios

Responsável por criar a estrutura principal do sistema e pela opção 1.

Funções:

Criar a lista/estrutura que armazenará os sorteios.
Cadastrar um novo sorteio.
Guardar:
nome do prêmio;
lista de participantes;
vencedor.
Criar o menu principal e a opção 1 - Cadastrar sorteio.

Exemplo de responsabilidade:

sorteios = []

def cadastrar_sorteio():
    premio = input("Digite o nome do prêmio: ")

    sorteio = {
        "premio": premio,
        "participantes": [],
        "vencedor": None
    }

    sorteios.append(sorteio)
    print("Sorteio cadastrado com sucesso!")
👤 Pessoa 2 — Participantes e listagem

Responsável pelas opções 2 e 3.

Funções:

Adicionar participantes a um sorteio.
Procurar o sorteio pelo nome do prêmio.
Listar todos os sorteios.
Mostrar os participantes.
Mostrar "Não definido" quando ainda não houver vencedor.

Exemplo:

def adicionar_participante():
    premio = input("Digite o nome do prêmio: ")
    nome = input("Digite o nome do participante: ")

    for sorteio in sorteios:
        if sorteio["premio"] == premio:
            sorteio["participantes"].append(nome)
            print("Participante adicionado ao sorteio!")
            return

    print("Sorteio não encontrado.")

E:

def listar_sorteios():
    print("\n========== SORTEIOS ==========")

    for sorteio in sorteios:
        print(f"\nPrêmio: {sorteio['premio']}")
        print("Participantes:")

        for participante in sorteio["participantes"]:
            print(f"- {participante}")

        vencedor = sorteio["vencedor"] or "Não definido"
        print(f"Vencedor: {vencedor}")
👤 Pessoa 3 — Vencedor, resultado e integração

Responsável pelas opções 4 e 5, além de ajudar a juntar tudo no menu final.

Funções:

Registrar o vencedor.
Verificar se o participante realmente está cadastrado no sorteio.
Consultar o resultado.
Mostrar o vencedor.
Integrar todas as funções no menu principal.

Exemplo:

def registrar_vencedor():
    premio = input("Digite o nome do prêmio: ")
    vencedor = input("Digite o nome do participante vencedor: ")

    for sorteio in sorteios:
        if sorteio["premio"] == premio:
            if vencedor in sorteio["participantes"]:
                sorteio["vencedor"] = vencedor
                print("Vencedor registrado com sucesso!")
            else:
                print("Participante não está cadastrado.")
            return

    print("Sorteio não encontrado.")

Resultado:

def consultar_resultado():
    premio = input("Digite o nome do prêmio: ")

    for sorteio in sorteios:
        if sorteio["premio"] == premio:
            print("\n========== RESULTADO ==========")
            print(f"Prêmio: {sorteio['premio']}")
            print(f"Vencedor: {sorteio['vencedor'] or 'Não definido'}")
            return

    print("Sorteio não encontrado.")
