# Nota-Fiscal-Python
```Python
op = 1
quant = []
prodnf = []
nome = [
    'lapis',
    'caneta',
    'borracha',
    'regua',
    'caderno'
]
preco = [
    0.7,
    1,
    2.2,
    5.2,
    25
]
reg = 6
regnf = 1
dc = 'S'

while (op != 0):
  print('\n1-Cadastrar Produto\n2-Relatório Produtos\n3-Cadastrar Nota Fiscal\n4-Relatório Nota Fiscal\n0-Sair')
  op = int(input('\nEscolha a opção: '))

  if op == 1:
    while (dc == 'S'):
      print('\nCadastro: ')
      nome.append(input(f'{reg}º Produto: '))
      preco.append(float(input('Preço: ')))
      dc = input('\nDeseja continuar cadastrando? (S/N): ').upper()
      reg += 1

  elif op == 2:
    print('\nRelatório: ')

    for i in range(reg - 1):
        print(f'\n{i + 1} | Nome: {nome[i]} | preço: {preco[i]}')

  elif op == 3:
    print('\nCadastrar NF:')
    produtos_nota = []
    mais_produtos = 'S'
    while mais_produtos.upper() == 'S':
      idprod = int(input('ID do Produto: '))
      if idprod >= 1 and idprod <= reg:
        quantt = int(input('quantidade: '))
        produtos_nota.append((idprod, nome[idprod - 1], preco[idprod - 1], quantt))
      else:
        print('ID de produto inválido!')
      mais_produtos = input('Deseja adicionar mais produtos na mesma nota fiscal? (S/N): ')
    prodnf.append(produtos_nota)
    print(f'Nota fiscal {regnf} cadastrada com sucesso!')
    regnf += 1

  elif op == 4:
    print('\nRelatório Nota Fiscal:')
    if prodnf:
      num_nf = int(input("Digite o número da nota fiscal que deseja visualizar: "))
      if num_nf >= 1 and num_nf <= regnf:
        print(f"\nNota Fiscal {num_nf}:")
        for i, item in enumerate(prodnf[num_nf - 1], 1):
          idprod, nomeprod, precoprod, quantt = item
          totali = precoprod * quantt
          print(f'Código: {idprod} \t| Nome: {nomeprod} \t| Preço unitário: R$ {precoprod:.2f} \t| quantidade: {quantt} \t| Total: R$ {totali:.2f}')
      else:
        print('Número de nota fiscal inválido!')
    else:
      print("Não há notas fiscais cadastradas.")

  elif op == 0:
    print('\nSair!')

  else:
    print('\nInformação inválida...')
```
