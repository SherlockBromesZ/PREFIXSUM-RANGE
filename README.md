

Imagine que você tem um monte de números e quer saber a soma de alguns pedaços específicos desse monte. É como ter uma fila de pessoas e querer saber o peso total de algumas pessoas do meio da fila, sem precisar somar o peso de cada uma delas individualmente. 🤔

Esse código faz exatamente isso! Ele é como um mágico que tira somas de intervalos da cartola. 🎩✨

Primeiro, ele define um array `a` com os números que você quer somar. Depois, ele cria um array `pf` que é tipo um mapa do tesouro. 🗺️ Ele guarda a "soma acumulada" dos elementos de `a`. Por exemplo, `pf[1]` é a soma de `a[0]` e `a[1]`, `pf[2]` é a soma de `a[0]`, `a[1]` e `a[2]`, e assim vai.

Aí vem a parte divertida: as "queries"! Elas são como pedidos que a gente faz pro código. Cada query tem dois números, que são os limites do intervalo que a gente quer somar. Por exemplo, a query `{2,3}` quer saber a soma dos elementos de `a` entre as posições 2 e 3 (que seriam `a[2]` e `a[3]`).

E como o código descobre essa soma? Fácil! Ele pega o valor de `pf` na posição final do intervalo e subtrai o valor de `pf` na posição anterior ao início do intervalo. É como se a gente cortasse um pedaço do mapa do tesouro e só olhasse para aquele pedaço. 💰

No final, o código imprime as respostas das queries, e todo mundo fica feliz. 🎉

```cpp
#include<bits/stdc++.h>
using namespace std;

int main() {
    ios_base::sync_with_stdio(false);
    cin.tie(NULL);
    
    int a[] = {1,2,3,4,5,6};
    int pf[6];
    
    // Calculando a soma prefixada
    for(int i = 1; i < 6; i++){
        pf[i] = pf[i-1] + a[i];
    }
    
    // Definindo as queries
    vector<vector<int>> query = {{2,3}, {3,4}, {1,2}};
    
    // Processando cada query
    for(int i = 0; i < 3; i++){
        int left = query[i][0];
        int right = query[i][1];
        
        // Imprimindo a soma do intervalo
        if(left == 1){
            cout << pf[right-1] << endl;
        }
        else{
            cout << pf[right-1] - pf[left-2] << endl;
        }
    }
    return 0;
}
```
