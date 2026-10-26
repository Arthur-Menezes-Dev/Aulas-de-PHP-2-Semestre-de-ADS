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


## Design Patterns
> Ver sobre o Design Patters (Gang of Four)
> [Design Patterns na Alura](https://www.alura.com.br/artigos/design-patterns-introducao-padroes-projeto?srsltid=AU7gw4VD1Ery-D8wzwKZXlQWfwJ2qdacfoT_Dl4-J0jzgbf32MIhl0J9)
