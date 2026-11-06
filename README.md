# Aulas-de-PHP-2-Semestre-de-ADS
Resumo das Aulas de php do segundo semestre da faculdade de analise e desenvolvimento de sistemas 

# Aula-PHP

> Os arquivos são os códigos que eu testei em aula.
> Link sobre os padrões de variáveis: [Padrões de Variáveis](https://www.alura.com.br/artigos/convencoes-nomenclatura-camel-pascal-kebab-snake-case?)

## Comando `Switch` `Case`
```php
<?php
  echo "Escolha a opção desejada: ";
  $opcao = fgets(STDIN);
  
  switch($opcao) {
    case 1:
      echo "Você escolheu a opção de CADASTRAR" . PHP_EOL;
      break;
    case 2:
      echo "Você escolheu a opção de MOSTRAR" . PHP_EOL;
      break;
    case 3:
      echo "Você escolheu a opção de EXCLUIR" . PHP_EOL;
      break;
    case 4:
      echo "Você escolheu a opção de SAIR" . PHP_EOL;
      break;
    default:
      echo "OPÇÃO INVÁLIDA!!!" . PHP_EOL;
  }
?>
```

## Comando `For`
```php
<?php
  for ($i = 0; $i <= 10; $i++) {
    echo "Valor da Variável i = " . $i . PHP_EOL;
  }
?>
```

## Comando `While`
```php
<?php
	$i = 0;
	while ($i <= 10) {
		echo "Valor da variável i = " . $i . PHP_EOL;
		$i++;
	}
?>
```
## Comando `Do - While`
> Executa primeiro o `do` depois verifica o `while`
```php
<?php
	$i = 0;
	do {
		echo "Valor da variável i = " . $i . PHP_EOL;
		$i++;
	} while ($i <= 10);

	echo "Valor final da variável i = " . $i;
?>
```

## Maneiras de Fazer operações
```php
<?php
	$valor = 10;
	$valor = $valor + 1;
	$valor++; // Somente se for de 1 em 1
	$valor += 1;  // Somente quando quiser efetuar cálculo com a variável e o resultado ser armazenado dentro da própria variável. Pode ser utilizado com outros operadores aritméticos. Bem como para o decremento.

	$valor = $valor+2;
	$valor += 2;
	$valor -= 2;
	$valor *= 2;
	$valor /= 2;
?>
```

## Criando Classes
> Arquivo `Carro.php`
```php
<?php
	class Carro {
		
		// Propriedade ou Atributo
		public $marca;
		public $modelo;
		public $cor;
		public $km;
		public $capacidadeTanque;
		public $kmPorLitro;

		// Método
		public function calcularKm() {
			return $this->capacidadeTanque * $this->kmPorLitro;
		}
	}
?>
```

## Utilizando Classe
```php
<?php
	include 'Carro.php';

	$novoCarro = new Carro();
	$novoCarro->marca = "VW";
	$novoCarro->modelo = "Fox";
	$novoCarro->cor = "Azul";
	$novoCarro->km = 15560;
	$novoCarro->capacidadeTanque = 50;
	$novoCarro->kmPorLitro = 12;

	echo "Marca: " . $novoCarro->marca . PHP_EOL;
	echo "Modelo: " . $novoCarro->modelo . PHP_EOL;
	echo "Cor: " . $novoCarro->cor . PHP_EOL;
	echo "Km: " . $novoCarro->km . PHP_EOL . PHP_EOL;
	echo "Função calcularKm(): " . $novoCarro->calcularKm();
?>
```

## Arrays e `Foreach`
```php
<?php
	
	// Cria o Vetor (Array), e insere os valores dentro do vetor
	$temperaturas = [15, 20, 18, 22, 30, 27, 24];
	$temperaturas[4] = 40;

	for ($i=0; $i<count($temperaturas); $i++) {
		echo "Dia " . ($i+1) . " : " . $temperaturas[$i] . PHP_EOL;
	}

	echo "\n";

	foreach ($temperaturas as $temperatura) {
		echo "Dia: " . $temperatura . PHP_EOL;
	}

?>
```

## Arrays (Listas) associativos
```php
<?php
	
	// Cria o Vetor (Array) associativos
	$temperaturas = [
		"domingo" => 20,
		"segunda" => 35,
		"terça" => 30,
		"quarta" => 26,
		"quinta" => 20,
		"sexta" => 28,
		"sabado" => 32
	];

	echo "Domingo: " . $temperaturas["domingo"] . PHP_EOL;
	echo "Segunda: " . $temperaturas["segunda"] . PHP_EOL;
	echo "Terça: " . $temperaturas["terça"] . PHP_EOL;
	echo "Quarta: " . $temperaturas["quarta"] . PHP_EOL;
	echo "Quinta: " . $temperaturas["quinta"] . PHP_EOL;
	echo "Sexta: " . $temperaturas["sexta"] . PHP_EOL;
	echo "Sabado: " . $temperaturas["sabado"] . PHP_EOL;

?>
```

## Atributos e Métodos Estáticos
> Os atributos e métodos estáticos executam e armazenam informações referentes à classe e que podem ser compartilhadas entre os objetos, ou seja, a informação não precisa pertencer a um único obj.
```php
<?php
	
	include "Carro.php";
	
	$novoCarro = new Carro("VW", "Fox", "Azul");
	$novoCarro->mostrarDados();

	echo "\n";

	$novoCarro2 = new Carro("Chevrolet", "Onix", "Preto");
	$novoCarro2->mostrarDados();

	echo "\n";

	$novoCarro3 = new Carro("Fiat", "Palio", "Prata");
	$novoCarro3->mostrarDados();

	echo "\n";

	//  Chamando o Método Estático
	echo "Quantidade de Carros: " . Carro::getQtCarros();

?>
<?php
	
	Class Carro {
		private $marca;
		private $modelo;
		private $cor;
		private static $qtCarros; // Atributo estático

		// Construtor
		public function __construct($marca, $modelo, $cor) {
			$this->marca = $marca;
			$this->modelo = $modelo;
			$this->cor = $cor;
			self::$qtCarros++;
		}

		public function getMarca() { return $this->marca; }
		public function getModelo() { return $this->modelo; }
		public function getCor() { return $this->cor; }

		// Método Estático
		public static function getQtCarros() {
			return self::$qtCarros;
		}

		public function mostrarDados() {
			echo "Marca: " . $this->getMarca() . PHP_EOL;
			echo "Modelo: " . $this->getModelo() . PHP_EOL;
			echo "Cor: " . $this->getCor() . PHP_EOL;
		}

	}

?>
```

## Herança `extends`
> Classe `Vendedor` *herda* atributos e métodos da Classe `Funcionario`
> 
> `class Vendedor extends Funcionario {}`
```php
<?php
	
	include "Funcionario.php";
	include "Vendedor.php";

	$func = new Funcionario();
	$func->setMatricula(1010);
	$func->setNome("Pedro");
	$func->setSalarioBruto(3000);

	echo "Matricula: " . $func->getMatricula() . PHP_EOL;
	echo "Nome: " . $func->getNome() . PHP_EOL;
	echo "Salário: " . $func->getSalarioBruto() . PHP_EOL;
	echo "Bonificação: " . $func->calcularBonificacao() . PHP_EOL;
	echo "Salário + bonificação: " . ($func->getSalarioBruto() + $func->calcularBonificacao()) . PHP_EOL;

	echo "\n";

	$vend = new Vendedor();
	$vend->setMatricula(2020);
	$vend->setNome("Francisca");
	$vend->setSalarioBruto(3000);

	echo "Matricula: " . $vend->getMatricula() . PHP_EOL;
	echo "Nome: " . $vend->getNome() . PHP_EOL;
	echo "Salário: " . $vend->getSalarioBruto() . PHP_EOL;
	echo "Bonificação: " . $vend->calcularBonificacao() . PHP_EOL;
	echo "Comissão: " . $vend->calcularComissao() . PHP_EOL;
	echo "Salário + bonificação + comissão: " . ($vend->getSalarioBruto() + $vend->calcularBonificacao() + $vend->calcularComissao());
	
?>
<?php
	class Funcionario {

		private $matricula;
		private $nome;
		private $salarioBruto;

		public function setMatricula($matricula) { $this->matricula = $matricula; }
		public function getMatricula() { return $this->matricula; }

		public function setNome($nome) { $this->nome = $nome; }
		public function getNome() { return $this->nome; }

		public function setSalarioBruto($salarioBruto) { $this->salarioBruto = $salarioBruto; }
		public function getSalarioBruto() { return $this->salarioBruto; }


		public function calcularBonificacao() {
			return $this->salarioBruto * 0.05;
		}
		
	}
?>
<?php

	class Vendedor extends Funcionario {

		public function calcularComissao() {
			return 100000 * 0.006;
		}

	}

?>
```








# PhP-Vetores
Aula de PhP 16/10/2026 Sobre Vetores 

## Vetor Básico com Numeros
```php
<?php
	
	$clima = []; // DEFINIDO COMO VETOR
	$clima[0] = 25;
	$clima[1] = 30;
	$clima[2] = 28;
	$clima[3] = 23;
	$clima[4] = 10;
	$clima[5] = 15;
	$clima[6] = 26;


	echo "Vetor: " . PHP_EOL;
	echo "posição 0: " . $clima[0] . PHP_EOL;
	echo "posição 1: " . $clima[1] . PHP_EOL;
	echo "posição 2: " . $clima[2] . PHP_EOL;
	echo "posição 3: " . $clima[3] . PHP_EOL;
	echo "posição 4: " . $clima[4] . PHP_EOL;
	echo "posição 5: " . $clima[5] . PHP_EOL;
	echo "posição 6: " . $clima[6] . PHP_EOL;



?>
```

## Vetor Básico com Palavras e Comando For e Foreach
```php
<?php
	
	$Produto = []; // DEFINIDO COMO VETOR
	$Produto[0] = "Arroz";
	$Produto[1] = "Feijão";
	$Produto[2] = "Macarrão";
	$Produto[3] = "Feijão de Corda";
	$Produto[4] = "Batata";
	$Produto[5] = "Salada";
	$Produto[6] = "Picanha";

	echo "Vetor: " . PHP_EOL;

  // For

  for($i=0;$i<7;$i++){
		echo "Posição $i: " . $Produto[$i] . PHP_EOL;
	}

  echo "\n";

  //Foreach

	foreach($Produto as $p){
		echo "Produto: " . $p . PHP_EOL;
	}

  /* Quando usar cada? A escrita do for é mais complexa que a do Foreach porem eu posso trabalhar com posição por posição de cada índice do vetor. O for conhece posição por posição do vetor
     o Foreach é mais simples na escrita e sempre vai mostrar todos os itens do vetor. Porem ele não trabalha/ mostra posição por posição. Ele mostra todos de uma vez só. */

?>
```

## Escrita Simplificada de Vetor
```php
<?php
	
	$Produto = ["Arroz","Feijão","Macarrão","Feijão de Corda","Batata","Salada","Picanha"]; // DEFINIDO COMO VETOR
	
	echo "Vetor: " . PHP_EOL;

	for($i=0;$i<7;$i++){
		echo "Posição $i: " . $Produto[$i] . PHP_EOL;
	}

	echo "\n";

	foreach($Produto as $p){
		echo "Produto: " . $p . PHP_EOL;
	}

?>
```

## Vetor Associativo
```php
<?php
	
	//VETOR ASSOCIATIVO (Chave e Valor)
	$Produto = [
		[
		"Nome"=> "Arroz",
		"Quantidade"=> 30
		],
		[
		"Nome"=> "Feijão",
		"Quantidade"=> 15
		],
		[
		"Nome"=> "Macarrão",
		"Quantidade"=> 10
		]
	];

	foreach($Produto as $p){
	echo "Nome do Produto: " . $p["Nome"] . PHP_EOL;
 	echo "Quantidade do Produto: " . $p["Quantidade"] . PHP_EOL;
	echo "\n";
	}

/* Colocamos um vetor dentro do outro*/
?>
```

## Vetores com objetos


//São 6 arquivos HelloWorld.php e Produtos.php

### Produtos.php
```php
<?php

class Produto{
	//PROPRIEDADES E ATRIBUTOS
	private $nome;
	private $quantidade;

	//CONSTRUTOR
	public function __construct ($nome, $quantidade){
		$this->nome = $nome;
		$this->quantidade = $quantidade;
	}

	//GETTERS 
	public function getNome(){
		return $this->nome;
	}

	public function getQuantidade(){
		return $this->quantidade;
	}
}

?>


```
###HelloWorld.php
```php
<?php

	include "Produto.php";

	$produtos = [	
		new Produto("Arroz", 10),
		new Produto("Feijão", 20),
		new Produto("Macarrão", 1,),
		new Produto("Batata", 30),
	];

	foreach($produtos as $p){
		echo "Nome do Produto: " . $p->getNome() . PHP_EOL;
		echo "Nome do Quantidade: " . $p->getQuantidade() . PHP_EOL;
		echo "\n";
	}

?>
```




# Herança-no-PHP
Aula do dia 14/10/2026 Sobre o conceito de herança na Programação Orientada a Objetos usando a linguagem PHP 

São 6 arquivos

HelloWorld.php
Funcionario.php
Vendedor.php
VendedorNivel1.php
VendedorNivel2.php
VendedorNivel3.php
Gerente.php

## HelloWorld.php
```php
<?php
   
    include "Funcionario.php";
    include "Vendedor.php";
    include "VendedorNivel1.php";
    include "VendedorNivel2.php";
    include "VendedorNivel3.php";
    include "Gerente.php";


    $func = new Funcionario();
    $func->setMatricula(1010);
    $func->setNome("Pedro");
    $func->setSalarioBruto(3000);


    echo "*********** " . get_class($func) . " **************" .PHP_EOL;
    echo "Matricula: " . $func->getMatricula() .PHP_EOL;
    echo "Nome: " . $func->getNome() . PHP_EOL;
    echo "Salário: " . $func->getSalarioBruto() . PHP_EOL;
    echo "Bonificação (5%): " . $func->calcularBonificacao() . PHP_EOL;
    echo "Salário + Bonificação: " . ($func->getSalarioBruto() + $func->calcularBonificacao() . PHP_EOL);


    echo "\n";


    $vendedor1 = new VendedorNivel1();
    $vendedor1->setMatricula(2020);
    $vendedor1->setNome("Francisca");
    $vendedor1->setSalarioBruto(3000);


    echo "*********** " . get_class($vendedor1) . " **************" .PHP_EOL;
    echo "Matricula: " . $vendedor1->getMatricula() .PHP_EOL;
    echo "Nome: " . $vendedor1->getNome() . PHP_EOL;
    echo "Salário: " . $vendedor1->getSalarioBruto() . PHP_EOL;
    echo "Bonificação (5%): " . $vendedor1->calcularBonificacao() . PHP_EOL;
    echo "Comissão: " . $vendedor1->calcularComissao() .PHP_EOL;
    echo "Salário + Bonificação + Comissão: " . ($vendedor1->getSalarioBruto() + $vendedor1->calcularBonificacao()  + $vendedor1->calcularComissao() . PHP_EOL);


    echo "\n";


    $vendedor2 = new VendedorNivel2();
    $vendedor2->setMatricula(2021);
    $vendedor2->setNome("Roberto");
    $vendedor2->setSalarioBruto(3000);


    echo "*********** " . get_class($vendedor2) . " **************" .PHP_EOL;
    echo "Matricula: " . $vendedor2->getMatricula() .PHP_EOL;
    echo "Nome: " . $vendedor2->getNome() . PHP_EOL;
    echo "Salário: " . $vendedor2->getSalarioBruto() . PHP_EOL;
    echo "Bonificação (5%): " . $vendedor2->calcularBonificacao() . PHP_EOL;
    echo "Comissão: " . $vendedor2->calcularComissao() .PHP_EOL;
    echo "Salário + Bonificação + Comissão: "  . ($vendedor2->getSalarioBruto() + $vendedor2->calcularBonificacao()  + $vendedor2  ->calcularComissao() . PHP_EOL);


    echo "\n";


    $vendedor3 = new VendedorNivel3();
    $vendedor3->setMatricula(2022);
    $vendedor3->setNome("Paula");
    $vendedor3->setSalarioBruto(3000);


    echo "*********** " . get_class($vendedor3) . " **************" .PHP_EOL;
    echo "Matricula: " . $vendedor3->getMatricula() .PHP_EOL;
    echo "Nome: " . $vendedor3->getNome() . PHP_EOL;
    echo "Salário: " . $vendedor3->getSalarioBruto() . PHP_EOL;
    echo "Bonificação (5%): " . $vendedor3->calcularBonificacao() . PHP_EOL;
    echo "Comissão: " . $vendedor3->calcularComissao() .PHP_EOL;
    echo "Salário + Bonificação + Comissão: " . ($vendedor3->getSalarioBruto() + $vendedor3->calcularBonificacao()  + $vendedor3  ->calcularComissao() . PHP_EOL);


    echo "\n";


    $gerente = new Gerente();
    $gerente->setMatricula(2023);
    $gerente->setNome("Sandra");
    $gerente->setSalarioBruto(6500);


    echo "*********** " . get_class($gerente) . " **************" .PHP_EOL;
    echo "Matricula: " . $gerente->getMatricula() .PHP_EOL;
    echo "Nome: " . $gerente->getNome() . PHP_EOL;
    echo "Salário: " . $gerente->getSalarioBruto() . PHP_EOL;
    echo "Bonificação (5%): " . $gerente->calcularBonificacao() . PHP_EOL;
    echo "Comissão: " . $gerente->calcularComissao() .PHP_EOL;
    echo "Salário + Bonificação + Comissão: " . ($gerente->getSalarioBruto() + $gerente->calcularBonificacao()  + $gerente->calcularComissao() . PHP_EOL);

?>
```
## Funcionario.php

```php
<?php



class Funcionario{


    private $matricula;
    private $nome;
    private $salarioBruto;


    public function calcularBonificacao(){
        return $this->salarioBruto * 0.05;
    }


    public function getMatricula(){
        return $this->matricula;
    }


    public function getNome(){
        return $this->nome;
    }


    public function getSalarioBruto(){
        return $this->salarioBruto;
    }


    public function setMatricula($matricula){
        $this->matricula = $matricula;
    }


    public function setNome($nome){
        $this->nome = $nome;
    }


    public function setSalarioBruto($salarioBruto){
        $this->salarioBruto = $salarioBruto;
    }


}

?>
```

## Vendedor.php

```php
<?php


class Vendedor extends Funcionario{


    public function calcularComissao(){
        return 100000 * 0.006;
    }


}

?>
```

## VendedorNivel1.php

```php
<?php


class VendedorNivel1 extends Vendedor{
   
    public function calcularComissao(){
        return 100000 * 0.01;
    }


}

?>
```

## VendedorNivel2.php

```php
<?php


class VendedorNivel2 extends Vendedor{
   
    public function calcularComissao(){
        return 100000 * 0.006;
    }


}

?>
```

## VendedorNivel3.php

```php
<?php


class VendedorNivel3 extends Vendedor{


    public function calcularComissao(){
        return 100000 * 0.004;
    }


}

?>
```


## Gerente.php

```php
<?php


class Gerente extends Vendedor{


    public function calcularComissao(){
        return 300000 * 0.005;
    }

    	public function calcularBonificacao(){
		return parent::calcularBonificacao() + 500;
	}


}
?>
```




# Interfaces-PHP-
Interfaces PHP Aula de 21/10/2026


## Notificacao.PHP
```php
<?php

interface Notificacao{

	// metodos abstrato. (Não tem Implementação, Somente a assinatura do metodo.)
	/*na interface não abrimos chaves nem implementamos nada.*/
	public function enviarNotificacao($mensagem);
	
}

?>
```



## Gerente.PHP

```php
<?php

class Gerente extends Vendedor implements Notificacao{

	public function calcularComissao(){
		return 300000 * 0.005;
	}

	public function calcularBonificacao(){
		return parent::calcularBonificacao() + 500;
	}

	public function enviarNotificacao($mensagem){

		echo "Enviando email: " . $mensagem . PHP_EOL; 

	}
}
// Aqui sim colocamos a abertura e fechamento de chaves e oque a função fará. 
?>
```


## VendedorNivel1.PHP

```php
<?php

include "Notificacao.php";

class VendedorNivel1 extends Vendedor implements Notificacao{
	
	public function calcularComissao(){
		return 100000 * 0.01;
	}

	public function enviarNotificacao($mensagem){
		
		echo "Enviando email: " . $mensagem . PHP_EOL; 

	}

}
?>
```

## HelloWorld.PHP
```php
<?php
	
	include "Funcionario.php";
	include "Vendedor.php";
	include "VendedorNivel1.php";
	include "VendedorNivel2.php";
	include "VendedorNivel3.php";
	include "Gerente.php";

	$func = new Funcionario();
	$func->setMatricula(1010);
	$func->setNome("Pedro");
	$func->setSalarioBruto(3000);

	echo "*********** " . get_class($func) . " **************" .PHP_EOL;
	echo "Matricula: " . $func->getMatricula() .PHP_EOL;
	echo "Nome: " . $func->getNome() . PHP_EOL;
	echo "Salário: " . $func->getSalarioBruto() . PHP_EOL;
	echo "Bonificação (5%): " . $func->calcularBonificacao() . PHP_EOL;
	echo "Salário + Bonificação: " . ($func->getSalarioBruto() + $func->calcularBonificacao() . PHP_EOL);

	echo "\n";

	$vendedor1 = new VendedorNivel1();
	$vendedor1->setMatricula(2020);
	$vendedor1->setNome("Francisca");
	$vendedor1->setSalarioBruto(3000);

	echo "*********** " . get_class($vendedor1) . " **************" .PHP_EOL;
	echo "Matricula: " . $vendedor1->getMatricula() .PHP_EOL;
	echo "Nome: " . $vendedor1->getNome() . PHP_EOL;
	echo "Salário: " . $vendedor1->getSalarioBruto() . PHP_EOL;
	echo "Bonificação (5%): " . $vendedor1->calcularBonificacao() . PHP_EOL;
	echo "Comissão: " . $vendedor1->calcularComissao() .PHP_EOL;
	echo "Salário + Bonificação + Comissão: " 
	. ($vendedor1->getSalarioBruto() + $vendedor1->calcularBonificacao()  + $vendedor1->calcularComissao() . PHP_EOL);
	$vendedor1->enviarNotificacao("Melhor Equipe de Vendas!!!!!!" . PHP_EOL);

	echo "\n";

	$vendedor2 = new VendedorNivel2();
	$vendedor2->setMatricula(2021);
	$vendedor2->setNome("Roberto");
	$vendedor2->setSalarioBruto(3000);

	echo "*********** " . get_class($vendedor2) . " **************" .PHP_EOL;
	echo "Matricula: " . $vendedor2->getMatricula() .PHP_EOL;
	echo "Nome: " . $vendedor2->getNome() . PHP_EOL;
	echo "Salário: " . $vendedor2->getSalarioBruto() . PHP_EOL;
	echo "Bonificação (5%): " . $vendedor2->calcularBonificacao() . PHP_EOL;
	echo "Comissão: " . $vendedor2->calcularComissao() .PHP_EOL;
	echo "Salário + Bonificação + Comissão: " 
	. ($vendedor2->getSalarioBruto() + $vendedor2->calcularBonificacao()  + $vendedor2	->calcularComissao() . PHP_EOL);

	echo "\n";

	$vendedor3 = new VendedorNivel3();
	$vendedor3->setMatricula(2022);
	$vendedor3->setNome("Paula");
	$vendedor3->setSalarioBruto(3000);

	echo "*********** " . get_class($vendedor3) . " **************" .PHP_EOL;
	echo "Matricula: " . $vendedor3->getMatricula() .PHP_EOL;
	echo "Nome: " . $vendedor3->getNome() . PHP_EOL;
	echo "Salário: " . $vendedor3->getSalarioBruto() . PHP_EOL;
	echo "Bonificação (5%): " . $vendedor3->calcularBonificacao() . PHP_EOL;
	echo "Comissão: " . $vendedor3->calcularComissao() .PHP_EOL;
	echo "Salário + Bonificação + Comissão: " 
	. ($vendedor3->getSalarioBruto() + $vendedor3->calcularBonificacao()  + $vendedor3	->calcularComissao() . PHP_EOL);

	echo "\n";

	$gerente = new Gerente();
	$gerente->setMatricula(2023);
	$gerente->setNome("Sandra");
	$gerente->setSalarioBruto(6500);
	

	echo "*********** " . get_class($gerente) . " **************" .PHP_EOL;
	echo "Matricula: " . $gerente->getMatricula() .PHP_EOL;
	echo "Nome: " . $gerente->getNome() . PHP_EOL;
	echo "Salário: " . $gerente->getSalarioBruto() . PHP_EOL;
	echo "Bonificação (5%): " . $gerente->calcularBonificacao() . PHP_EOL;
	echo "Comissão: " . $gerente->calcularComissao() .PHP_EOL;
	echo "Salário + Bonificação + Comissão: " 
	. ($gerente->getSalarioBruto() + $gerente->calcularBonificacao()  + $gerente->calcularComissao() . PHP_EOL);
	$gerente->enviarNotificacao("VAMOS BATER A META DO MÊS !!!!!!!!!!!!!!!!!!!!!!!!!!!");


?>
```




# php-na-rede-com-html
Aula de 30/10/2026 integração do html com php

## Usando Vs code e xampp no xampp apache ligado. online pesquise localhost/ o nome do seu arquivo. Se precisar misturar php com html vc deve colocar o arquivo como php. Ex: Arthur.php mesmop contendo o html nele tb. 

index.php

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>



    <h1>Uninove - Universidade Nove De Julho</h1>

    <?php 
        echo "<h2>Hoje estamos estudando PHP na Web</h2>" . "<br>";



        $idade = 18;

        if ($idade>=18){
            echo "Pode votar" ."<br>";
        } else {
            echo "não pode votar" ."<br>";
        }

        for($i=0;$i<=10;$i++){
            echo "valor da variavel i" .$i . "<br>";
        }
    ?>
    

</body>
</html>

## no vs code o PHP_EOL; não funciona. Só funciona o "<br>"


header.php

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>

indeex.php


<?php include "header.php"; ?>
<?php echo "<h1>Uninove - Universidade Nove De Julho</h1>"; ?>
<?php include "footer.php"; ?>







footer.php

</body>
</html>










<?php

namespace fornecedor_principal;

class Produto{

    public function mostrarDetalhes(){
        echo "Detalhes do Produto do Fornecedor";
    }
}
?>





<?php

namespace fornecedor_secundario;
class Produto{

    public function mostrarDetalhes(){
        echo "Detalhes do Produto do Fornecedor2";
    }
}
?>




<?php 

    require_once "header.php";
    require_once "fornecedor1/produto.php";
    require_once "fornecedor2/produto.php";

    use fornecedor_principal\Produto;

    echo "ola mundo" ."<br>";
    $produto = new Produto();
    $produto->mostrarDetalhes();

    require_once "footer.php";

    ?>









<?php 

    require_once "header.php";
    require_once "fornecedor1/produto.php";
    require_once "fornecedor2/produto.php";


    echo "ola mundo" ."<br>";
    $produto = new fornecedor_principal\Produto();
    $produto->mostrarDetalhes();

    echo "ola mundo" ."<br>";
    $produto = new fornecedor_secundario\Produto();
    $produto->mostrarDetalhes();

    require_once "footer.php";

?>


# Aula 06/11/2026 MVC

Php -> Controlador (Backend) Visão (Front-end) Modelo (Banco de dados) Saiba deles Caso haja problema no seu site, voce sabe onde corrigir. Isso é MVC 

arquivos: index.php pasta: view -> arquivo: produto.php Pasta controler -> ProdutoControler.php arquivo:  Pasta: model-> arquivo:  listadeproduto.php

## index.php

<?php 

    require_once "controler/ProdutoControler.php";

    $controler = new ProdutoControler();
    $controler->listaProdutos();



    ?>



## produto.php

<?php

namespace model/produto.php ;

class produto{
    private $codigo;
    private $produto;
    private $precoUnitario;

    public function __construct($codigo,$produto,$precoUnitario){
        $this->codigo = $codigo;
        $this->$produto = $produto;
        $this->$precoUnitario = $precoUnitario;
    }

    public function getCodigo(){
        return $this->codigo;
    }

    
    public function getProduto(){
        return $this->produto;
    }

    
    public function getPrecoUnitario(){
        return $this->precoUnitario;
    }
}

?>






## ProdutoControler.php



<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Lista de Produtos</title>
</head>
<body>

    <h1>Lista de Produtos</h1>

    <table border="1" style="width: 50%;">

        <thead>
            <tr style="background-color: black;color: white;">
                <th>Codigo</th>
                <th>Produto</th>
                <th>Preço Unitario</th>
            </tr>
        </theade>

        <tbody>
                <?php foreach($produtos as $produto): ?>
                <tr>
                    <td><?php echo $produto->getCodigo(); ?></td>
                    <td><?php echo $produto->getProduto(); ?></</td>
                    <td><?php echo $produto->getPrecoUnitario(); ?></</td>
                </tr>
                <?php endforeach; ?>
        </tbody>
    </table>
    
</body>
</html>


## listadeproduto.php

<? 

use \model\Produto;

class PRodutoControler{

    public function listarProdutos(){

        $produtos = [
            new Produto(1,"Produto A", 10.00),
            new Produto(2,"Produto B", 15.50),
            new Produto(3,"Produto C", 20.00),
            new Produto(4,"Produto D", 40.00)
        ];

        include "view/listadeprodutos.php";

    }

}




## Design Patterns
> Ver sobre o Design Patters (Gang of Four)
> [Design Patterns na Alura](https://www.alura.com.br/artigos/design-patterns-introducao-padroes-projeto?srsltid=AU7gw4VD1Ery-D8wzwKZXlQWfwJ2qdacfoT_Dl4-J0jzgbf32MIhl0J9)
