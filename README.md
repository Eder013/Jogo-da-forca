programa {
  inclua biblioteca Texto --> txt

  // declarações globais
  cadeia palavra, continuar, letra, vetorDaPalava[100], letras[26]
  inteiro opcao, tentativas = 7, numChar, contLetra = 0, contAcertos = 0
  logico achoLetra = falso

  funcao inicio() {
    faca {
      escreva(":: JOGO DA FORCA ::\n\n")
      escreva("1 - Iniciar o jogo\n")
      escreva("0 - Siar do jogo\n")
      leia(opcao)

      escolha(opcao) {
        caso 1:
          iniciar()
        pare
      }
    } enquanto(opcao != 0)
  }

  funcao iniciar() {
    limpa()
    escreva(":: JOGO DA FORCA ::\n\n")
    escreva("Para começar, digite a palavra: \n")
    leia(palavra)

    limpa()
    escreva("Maravilha! Palavra definida!\nVamos começar...")
    escreva("\n\nPresione 'enter' para continuar")
    leia(continuar)

    novaLetra()
  }

  funcao novaLetra() {
    escreva("\n\n")
    listarPalavra()

    enquanto(tentativas >= 0) {
      limpa()
      escreva(":: JOGO DA FORCA ::\n\n")
      escreva("\nA palavra possui ", numChar, " letras \n\n")
      listarTentativas()
      montarBoneco()

      se(tentativas == 100) { // condição que ganha o jogo
        escreva("\n\nVocê acertou!\n\n")
        escreva("Digite 'enter' para recomeçar")
        leia(continuar)
        iniciar()
      } senao {
        escreva("\n\nVocê tem ", tentativas, " tentativas!!!\n\n")
        escreva("Digite uma letra: ")
        leia(letra)
        atualizarTentativas(letra)
        contLetra++
      }
    }
  }

  funcao atualizarTentativas(cadeia letra) {
    escreva(":: JOGO DA FORCA ::\n\n")
    escreva("\nA palavra possui ", numChar, " letras: \n\n")
    
    para(inteiro i = 0; i < numChar; i++) {
      se(txt.obter_caracter(palavra, i) == letra) {
        vetorDaPalava[i] = letra + " "
        achoLetra = verdadeiro
        contAcertos++
        
        se(contAcertos == numChar) { // verifica se acertou todas as letras
          tentativas = 100
        }
      }
      escreva(vetorDaPalava[i])
    }

    se(achoLetra == falso) {
      tentativas--
    }

    achoLetra = falso
  }

  funcao listarTentativas() {
    para(inteiro i = 0; i < numChar; i++) {
      escreva(vetorDaPalava[i], " ")
    }

    se(contLetra > 0) {
      letras[contLetra] = letra
      escreva("\n______________\n")
      escreva("Letras digitadas: ", contLetra, "\n\n")
      para(inteiro i = 1; i <= contLetra; i++) {
        escreva(letras[i], " | ")
      }
      escreva("\n______________\n")
    }
  }
 
  funcao listarPalavra() {
    numChar = txt.numero_caracteres(palavra)

    para(inteiro i = 0; i < numChar; i++) {
      vetorDaPalava[i] = "_ "
      escreva(vetorDaPalava[i])
    }
  }

  funcao montarBoneco() {
    escreva("\n\n")
    se(tentativas == 100) {
      escreva(" ______\n")
      escreva("|      |\n")
      escreva("|\n")
      escreva("|\n")
      escreva("|      Õ\n")
      escreva("|     L|/\n")
      escreva("|_____/ L___\n")
    }
    se(tentativas == 7) {
      escreva(" ______\n")
      escreva("|      |\n")
      escreva("|\n")
      escreva("|\n")
      escreva("|\n")
      escreva("|\n")
      escreva("|_\n")
    }
    se(tentativas == 6) {
      escreva(" ______\n")
      escreva("|      |\n")
      escreva("|      Õ\n")
      escreva("|\n")
      escreva("|\n")
      escreva("|\n")
      escreva("|_\n")
    }
    se(tentativas == 5) {
      escreva(" ______\n")
      escreva("|      |\n")
      escreva("|      Õ\n")
      escreva("|      |\n")
      escreva("|\n")
      escreva("|\n")
      escreva("|_\n")
    }
    se(tentativas == 4) {
      escreva(" ______\n")
      escreva("|      |\n")
      escreva("|      Õ\n")
      escreva("|    --|\n")
      escreva("|\n")
      escreva("|\n")
      escreva("|_\n")
    }
    se(tentativas == 3) {
      escreva(" ______\n")
      escreva("|      |\n")
      escreva("|      Õ\n")
      escreva("|    --|--\n")
      escreva("|\n")
      escreva("|\n")
      escreva("|_\n")
    }
    se(tentativas == 2) {
      escreva(" ______\n")
      escreva("|      |\n")
      escreva("|      Õ\n")
      escreva("|    --|--\n")
      escreva("|     / \n")
      escreva("|\n")
      escreva("|_\n")
    }
    se(tentativas == 1) {
      escreva(" ______\n")
      escreva("|      |\n")
      escreva("|      Õ\n")
      escreva("|    --|--\n")
      escreva("|     / L\n")
      escreva("|\n")
      escreva("|_\n")
    }
    se(tentativas == 0) {
      escreva(" ______\n")
      escreva("|      |\n")
      escreva("|\n")
      escreva("|\n")
      escreva("|\n")
      escreva("|    --|--\n")
      escreva("|__Õ__/ L___\n")
    }
  }
}
