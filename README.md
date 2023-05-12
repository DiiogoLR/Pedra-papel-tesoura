#include <stdio.h>
#include <time.h>
#include <stdlib.h>

//O código funciona a partir da base da tabela verdade: 1- PEDRA, 2- PAPEL, 3- TESOURA
//POSSIBILIDADES: 1 e -1 = 0 (-1 para não ficar respostas altas e assim criando um padrão)
//1 e -2; 1 e -3; 2 e -1; 2 e -2; 2 e -3; 3 e -1; 3 e -2; 3 e -3;
//Empate (0); Vitória do computador (-1 e 2); Vitória do Usuário (1 e -2)

    void delay(unsigned int secs) {
    unsigned int end_time = time(NULL) + secs;
    while (time(NULL) < end_time);                   // Delay utilizado pra substituir o uso do "sleep", o qual não funcionou nessa plataforma
}

int main() {
  
  int Esc_Usuario, Esc_Computador,soma_resposta,vitoriaC=0,vitoriaU=0;   //Variáveis utilizadas

while((vitoriaC<3) && (vitoriaU<3)){  //Laço de repetição para contar as vitórias de cada jogador
  
  srand(time(NULL));
  Esc_Computador = rand()%3;   //Randomizar respostas do PC
  
  printf("Placar:\n Serumaninho %d\n Computador %d\n", vitoriaU, vitoriaC); //Placar
  printf("\nEscolha \n 1- Pedra\n 2- Papel\n 3- Tesoura \n");  //Menu 
  scanf("%d", &Esc_Usuario);

  printf("o computador jogou %d\n",Esc_Computador+1);
  Esc_Computador = (Esc_Computador+1)*(-1);  //Expressão usada para inserir a resposta randomizada do computador no padrão de respostas a partir da tabela verdade das possibilidades
  
  soma_resposta = Esc_Usuario + (Esc_Computador); //Variável lógica para indicar a vitória em cada rodada
  
  if(soma_resposta == 0){
    printf("Empate na rodada! \n");
    delay(2);
    system ("clear"); //Com o uso do Linux nessa plataforma, é necessário o uso do system("clear"), ao invés de system("cls") que é usado para windows
  }
      if(soma_resposta == -1 || soma_resposta == 2){
      printf("O computador ganhou a rodada!-------- \n");
        vitoriaC++;    //Incrementa mais 1 no contador de vitórias nas rodadas
        delay(2);
        system ("clear");
      }
        else if(soma_resposta == 1 || soma_resposta == -2){
        printf("O Serumaninho ganhou a rodada! ------------------------ \n");
          vitoriaU++;
          delay(2);
          system ("clear");
        }
  }
  if(vitoriaC==3){                                                                                           //Tabela ASCII "Derrota"
    printf("o Computador ganhou!!!\n\n");
     printf("d8888b.      d88888b      d8888b.      d8888b.       .d88b.       d888888b       .d8b.\n");
       delay(1);
  printf("88  `8D      88'          88  `8D      88  `8D      .8P  Y8.      `~~88~~'      d8' `8b\n");
       delay(1);
  printf("88   88      88ooooo      88oobY'      88oobY'      88    88         88         88ooo88 \n");
       delay(1);
  printf("88   88      88~~~~~      88`8b        88`8b        88    88         88         88~~~88 \n");
       delay(1);
  printf("88  .8D      88.          88 `88.      88 `88.      `8b  d8'         88         88   88\n"); 
       delay(1);
  printf("Y8888D'      Y88888P      88   YD      88   YD       `Y88P'          YP         YP   YP\n");
      }
  else{printf("o serumaninho ganhou!!!!\n\n");                                                               //Tabela ASCII "Vitória"
    printf("db    db      d888888b      d888888b       .d88b.       d8888b.      d888888b       .d8b.  \n");
       delay(1);
  printf("88    88        `88'        `~~88~~'      .8P  Y8.      88  `8D        `88'        d8' `8b \n");
       delay(1);
  printf("Y8    8P         88            88         88    88      88oobY'         88         88ooo88 \n");
       delay(1);
  printf("`8b  d8'         88            88         88    88      88`8b           88         88~~~88 \n");
       delay(1);
  printf(" `8bd8'         .88.           88         `8b  d8'      88 `88.        .88.        88   88 \n"); 
       delay(1);
  printf("   YP         Y888888P         YP          `Y88P'       88   YD      Y888888P      YP   YP \n");
      }
}
