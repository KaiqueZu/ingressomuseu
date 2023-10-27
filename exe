#include <stdio.h>
#include <stdlib.h>
#include <string.h>

// Estrutura para armazenar informações sobre as exposições
typedef struct Exhibition {
    char name[100];
    float ticketPrice;
    int ticketsSold;
} Exhibition;

// Função para vender ingressos
void sellTickets(Exhibition *exhibitions, int numExhibitions) {
    printf("Escolha a exposicao desejada:\n");
    for (int i = 0; i < numExhibitions; i++) {
        printf("%d. %s - Preco do ingresso: R$%.2f\n", i + 1, exhibitions[i].name, exhibitions[i].ticketPrice);
    }

    int choice;
    printf("Digite o numero da exposicao: ");
    scanf("%d", &choice);

    if (choice < 1 || choice > numExhibitions) {
        printf("Escolha invalida.\n");
        return;
    }

    int numTickets;
    printf("Digite o numero de ingressos a serem comprados: ");
    scanf("%d", &numTickets);

    if (numTickets <= 0) {
        printf("Quantidade invalida de ingressos.\n");
        return;
    }

    exhibitions[choice - 1].ticketsSold += numTickets;
    printf("%d ingressos para a exposicao %s vendidos com sucesso!\n", numTickets, exhibitions[choice - 1].name);
    
    // Atualize o arquivo CSV com as informações de vendas
    FILE *csvFile = fopen("vendas.csv", "a");
    if (csvFile != NULL) {
        fprintf(csvFile, "%s,%d\n", exhibitions[choice - 1].name, numTickets);
        fclose(csvFile);
    }
}

// Função para mostrar a quantidade de ingressos vendidos
void showTicketsSold(Exhibition *exhibitions, int numExhibitions) {
    for (int i = 0; i < numExhibitions; i++) {
        printf("%s - Ingressos vendidos: %d\n", exhibitions[i].name, exhibitions[i].ticketsSold);
    }
}

int main() {
    int numExhibitions = 2;
    Exhibition exhibitions[numExhibitions];
    
    // Inicialize as informações das exposições
    strncpy(exhibitions[0].name, "Exposicao 1:150 anos de Santos Dumont", sizeof(exhibitions[0].name));
    exhibitions[0].ticketPrice = 10.0;
    exhibitions[0].ticketsSold = 0;

    strncpy(exhibitions[1].name, "Exposicao 2:Jogos Olímpicos de Paris 2024", sizeof(exhibitions[1].name));
    exhibitions[1].ticketPrice = 15.0;
    exhibitions[1].ticketsSold = 0;

    int choice;
    while (1) {
        printf("\nSelecione uma opcao:\n");
        printf("1. Vender ingressos\n");
        printf("2. Mostrar quantidade de ingressos vendidos\n");
        printf("3. Sair\n");
        scanf("%d", &choice);

        switch (choice) {
            case 1:
                sellTickets(exhibitions, numExhibitions);
                break;
            case 2:
                showTicketsSold(exhibitions, numExhibitions);
                break;
            case 3:
                printf("Saindo do programa.\n");
                exit(0);
            default:
                printf("Opcao invalida. Tente novamente.\n");
        }
    }

    return 0;
}
