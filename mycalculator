package mycalculator

import (
	"bufio"
	"fmt"
	"os"
	"regexp"
	"strconv"
)

type calc struct {
	e1 int
	e2 int
}

func (self calc) operate(operador string) int {
	operador1 := self.e1
	operador2 := self.e2

	var resultado int

	switch operador {
	case "+":
		resultado = operador1 + operador2
	case "-":
		resultado = operador1 - operador2
	case "*":
		resultado = operador1 * operador2
	case "/":
		if operador2 == 0 {
			fmt.Println("Error: Division entre cero")
			return 0
		}
		resultado = operador1 / operador2
	default:
		fmt.Println("Operador no aceptado")
		resultado = 0
	}

	return resultado
}

func parsear(entrada string) int {
	operador, _ := strconv.Atoi(entrada)
	return operador
}

func LeerEntrada() string {
	scanner := bufio.NewScanner(os.Stdin)
	scanner.Scan()

	return scanner.Text()
}

func getOperands(entrada string) (calc, string) {
	regex := regexp.MustCompile(`^(\d+)([\+\-\*\/])(\d+)$`)

	//entrada := leerEntrada()

	if regex.Match([]byte(entrada)) {
		entrada1 := parsear(regex.ReplaceAllString(entrada, "$1"))
		operador := regex.ReplaceAllString(entrada, "$2")
		entrada2 := parsear(regex.ReplaceAllString(entrada, "$3"))

		c := calc{e1: entrada1, e2: entrada2}
		//toPrint := c.operate(operador)
		return c, operador
		//fmt.Println(toPrint)
	} else {
		return calc{}, ""
	}

}
