# scanner-parser

## Grammer
line    -->     exit
line    -->     exp
line    -->     line exp
line    -->     line exit
line    -->     exp exit

exp    	-->     term
exp    	-->     exp AddOp term
exp     -->     exp MinOp term

term   	-->     factor
term    -->     factor MulOp term
term    -->     factor DivOp term

factor  -->     primary

primary -->     number
primary -->     startingParanthesis exp endingParanthesis


## Example Productions
(200+100) * (5 / 2);


line    -->     exp
        -->     term
        -->     factor MulOp term
        -->     primary MulOp term
        -->     ( exp ) MulOp term
        -->     ( exp AddOp term ) MulOp term
        -->     ( term AddOp term ) MulOp term
        -->     ( factor AddOp term ) MulOp term
        -->     ( number AddOp term ) MulOp term
        -->     ( 200 AddOp term ) MulOp term
        -->     ( 200 + term ) MulOp term
        -->     ( 200 + factor ) MulOp term
        -->     ( 200 + number ) MulOp term
        -->     ( 200 + 100 ) MulOp term
        -->     ( 200 + 100 ) * term
        -->     ( 200 + 100 ) * factor
        -->     ( 200 + 100 ) * primary
        -->     ( 200 + 100 ) * ( exp )
        -->     ( 200 + 100 ) * ( term )
        -->     ( 200 + 100 ) * ( factor DivOp term )
        -->     ( 200 + 100 ) * ( primary DivOp term )
        -->     ( 200 + 100 ) * ( number DivOp term )
        -->     ( 200 + 100 ) * ( 5 DivOp term )
        -->     ( 200 + 100 ) * ( 5 / term )
        -->     ( 200 + 100 ) * ( 5 / factor )
        -->     ( 200 + 100 ) * ( 5 / primary )
        -->     ( 200 + 100 ) * ( 5 / number )
        -->     ( 200 + 100 ) * ( 5 / 2 )


4+5     *     2;

line    -->     exp
        -->     term
        -->     exp AddOp term
        -->     term AddOp term
        -->     factor AddOp term
        -->     primary AddOp term
        -->     number AddOp term
        -->     4 AddOp term
        -->     4 + term
        -->     4 + term
        -->     4 + factor MulOp term
        -->     4 + primary MulOp term
        -->     4 + number MulOp term
        -->     4 + 5 MulOp term
        -->     4 + 5 * factor
        -->     4 + 5 * primary
        -->     4 + 5 * number
        -->     4 + 5 * 2

        

