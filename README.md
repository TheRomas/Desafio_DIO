# Desafio_DIO
menu = """

[d] Depositar
[s] Sacar
[e] Extrato
[q] Sair

""" '\n'

saldo = 1500
extrato = []
saques_diarios = 3
LIMITE_DE_SAQUE = 500

while True:
    opcao = input(menu)

    if opcao == "d":
        valor = float(input("Digite o valor a ser depositado: "))
        if valor > 0:
            saldo += valor
            extrato.append(f"Depósito: +R$ {valor:.2f}")
        else:
            print("Valor de depósito inválido.")
    elif opcao == "s":
        valor = float(input("Digite o valor a ser sacado: "))
        if saques_diarios > 0 and valor <= saldo and saques_diarios > 0 and LIMITE_DE_SAQUE > 0 and valor <= 500:
            saldo -= valor
            saques_diarios -= 1
            LIMITE_DE_SAQUE -= 1
            extrato.append(f"Saque: -R$ {valor:.2f}")
        elif valor > saldo:
            print("Saldo insuficiente.")
        elif valor > 500:
            print("valor de saque excede o limite maximo de R$500")
        else:
            print("Limite diário de saques atingido ou valor de saque inválido.")

    elif opcao == "e":
        if not extrato:
            print("Não foram realizadas movimentações.")
        else:
            for operacao in extrato:
                print(operacao)
        print(f"Saldo atual: R$ {saldo:.2f}")

    elif opcao == "q":
        print("Obrigado por usar nosso sistema")
        break
