# Oi-Paulo-Afonso
Olá professor, obrigada pela paciência, aqui está um **código em C++ para converter um arquivo .csv em .bin**

* A função *main* chama a função converte.
* A função *converte* ignora a primeira linha do arquivo, que se espera não conter dados.
* Enquanto o arquivo não chegar ao fim, o programa percorre linha por linha tratando o arquivo (removendo acentos, aspas e parênteses desnecessários) e as convertendo em binário e registrandoas em novo arquivo.

```
#include <iostream>
#include <fstream>
#include <string.h>
using namespace std;

struct dado{	
	char id[6];
	char nome[30];
	char cidade[20];
	char esporte[30];
	char evento[20];
	char noc[3];
};
//função converte;
void converte(){
	
	ifstream arquivoEntrada ("data_athlete_event.csv");
	ofstream arquivoSaida("saida.bin");
	int caracteres =0;
	unsigned contaVirgula =0, i=0, j=0;
	string linha;
	char informacao[30];
	dado registro;
	
	if(arquivoEntrada){
		cout<< "Iniciando conversao" << endl;
		getline(arquivoEntrada,linha); // descarta primeira linha
		while(getline(arquivoEntrada,linha)){
			contaVirgula =0;
			i=0;
			j=0;
			cout<< linha << endl;
			while(i<linha.size()){					
					if( linha[i]=='(' or linha[i]==')' or linha[i]=='-'){
						i++;
					}
					else if(linha[i]==','){
						if(linha[i+1]==' '){
							caracteres++;
							informacao[j]=linha[i];
							i++;
						}else{
							contaVirgula++;
							int k;
					
					switch(contaVirgula){
						case 1:
							for(k=0; k<caracteres;k++){
								registro.id[k]=informacao[k];
							}						
							if(arquivoSaida){
								arquivoSaida.write((char*)(&registro.id),sizeof(dado));
							}
							else{
								cout<< "Erro ao abrir arquivo de saida" <<endl;
							}
							break;
						case 2:
							for(k=0; k<caracteres;k++){
								registro.nome[k]=informacao[k];
							}
							if(arquivoSaida){
								arquivoSaida.write((char*)(&registro.nome),sizeof(dado));
							}
							else{
								cout<< "Erro ao abrir arquivo de saida" <<endl;
							}
							break;
						case 3:
							for(k=0; k<caracteres;k++){
								registro.cidade[k]=informacao[k];
							}
							if(arquivoSaida){
								arquivoSaida.write((char*)(&registro.cidade),sizeof(dado));
							}
							else{
							cout<< "Erro ao abrir arquivo de saida" <<endl;
							}
							break;
						case 4:
							for(k=0; k<caracteres;k++){
								registro.esporte[k]=informacao[k];
							}
							if(arquivoSaida){
								arquivoSaida.write((char*)(&registro.esporte),sizeof(dado));
							}
							else{
								cout<< "Erro ao abrir arquivo de saida" <<endl;
							}
							break;
						case 5:
							for(k=0; k<caracteres;k++){
								registro.evento[k]=informacao[k];
							}
							if(arquivoSaida){
								arquivoSaida.write((char*)(&registro.evento),sizeof(dado));
							}
							else{
								cout<< "Erro ao abrir arquivo de saida" <<endl;
							}
							break;
						case 6:
							for(k=0; k<caracteres;k++){
								registro.noc[k]=informacao[k];
							}
							if(arquivoSaida){
								arquivoSaida.write((const char*)(&registro.noc),sizeof(dado));
							}
							else{
								cout<< "Erro ao abrir arquivo de saida" <<endl;
							}
							break;
					}
			
			j=0;
			caracteres=0;			}
						
					}
			
			informacao[j]=linha[i];
			i++;
			}
		}	
		cout<< "Conversao concluída" << endl;
	}
	else{
		cout<< "Conversao falhou!" << endl;
	}
}


int main(){

		converte();
	
	return 0;
}

```
[Foca fofa](https://br.pinterest.com/pin/531776668502227222/ "Olha que link interessante aqui em baixo, eu clicava se fosse você!")

[Link importantíssimo!](https://www.youtube.com/watch?v=dQw4w9WgXcQ)
