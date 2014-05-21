EDCppT1Ej3
==========

#include <iostream>

using namespace std;

int s[10][10];

int simetrica(int fila, int col1, int col2)
{
	/* La función que mira la simetría de una matriz cuadrada será O(n^2/2), porque solo se recorre
	 * la mitad del array horizontalmente
	 */
	int r=1;
	if(col1<=col2)
	{
		r=(s[fila][col1] == s[fila][col2]);
		if(r)
		{
			if((col1 == col2)||((col1+1) == col2))
			{
				if(fila<9)
					r=simetrica(fila+1, 0, 9);
			}
			else
				r=simetrica(fila, col1+1, col2-1);
		}
	}
	return r;
}

int main()
{
    cout<<"Progrmama que mira la simetria de una matriz"<<endl;
    int i;
    int j;
    //Inicializaciónd de matrices
    cout<<"Matriz simétrica"<<endl;
    for(i=0;i<10;i++)
    { // For con complejidad O(n)
    	for(j=0; j<10; j++)
    	{ // For con complejidad O(n)
    		s[i][j]=i; /* asignamos a todas las pisiciones de una fila el número de fila,
						en cualquier columna de la primera fila, por ejemplo, el valor será 0 */
    		cout<<s[i][j];
    	}
    	cout<<endl;
    }/* complejidad de un for dentro de otro O(n^2) (se repetira el for de dentro n veces y el de fuera otras n,
    así que es complejidad O(n*n)=O(n^2)*/

    int resultado = simetrica(0, 0, 9);
    if(resultado)
    	cout<<"La matiz es simetrica"<<endl;
    else
    	cout<<"La matriz no es simetrica"<<endl;

    cin.get();
    return 0;
}
