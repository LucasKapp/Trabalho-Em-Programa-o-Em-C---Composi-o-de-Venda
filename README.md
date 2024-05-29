#include <stdio.h>
#include <string.h>

struct Item {
    int codigo;
    char nome[50];
    float preco;
};

int main() {
    int numItens;

    printf("Quantos itens você deseja inserir? ");
    scanf("%d", &numItens);

    struct Item itens[

    struct {
        int codigo;
        int inserido;
    } codigosInseridos[numItens];

    for (int i = 0; i < numItens; i++) {
        codigosInseridos[i].codigo = 0;
        codigosInseridos[i].inserido = 0;
    }

    for (int i = 0; i < numItens; i++) {
        printf("\nItem %d:\n", i + 1);
        printf("Código: ");
        scanf("%d", &itens[i].codigo);

        int codigoDuplicado = 0;
        for (int j = 0; j < i; j++) {
            if (codigosInseridos[j].codigo == itens[i].codigo && codigosInseridos[j].inserido == 1) {
                codigoDuplicado = 1;
                break;
            }
        }

        if (codigoDuplicado) {
            printf("Código já inserido. Insira um código diferente.\n");
            i--;
            continue;
        }

        codigosInseridos[i].codigo = itens[i].codigo;
        codigosInseridos[i].inserido = 1;

        printf("Nome: ");
        scanf("%s", itens[i].nome);

        printf("Preço: ");
        scanf("%f", &itens[i].preco);
    }

    printf("\nLista de Itens:\n");
    for (int i = 0; i < numItens; i++) {
        printf("Código: %d, Nome: %s, Preço: %.2f\n", itens[i].codigo, itens[i].nome, itens[i].preco);
    }

    float totalPreco = 0;
    for (int i = 0; i < numItens; i++) {
        totalPreco += itens[i].preco;
    }
    printf("\nTotal dos preços: %.2f\n", totalPreco);

    return 0;
}
