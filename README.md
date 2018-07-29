


Results 

X0 X1	  output
1	 1	  1
1	 0	  1
0	 1	  1
0	 0	  0


2. code 

import numpy as nmp

user_iput = []
x = 0

def perceptron(weight, bias, x):
    model = nmp.add( nmp.dot( x, weight ), bias )  # same as (x * weight) + bias
    outPut = 1 / (1 + nmp.exp( -model ))  # same as 2 ** -model
    return nmp.round( outPut )


def executePerceptron(gateType, weightDictionary, dataset):
    weights = nmp.array( [weightDictionary[gateType][w] for w in weightDictionary[gateType].keys()[::-1]] )
    output = nmp.array( [perceptron( weights, weightDictionary['bias'][gateType], val ) for val in dataset] )
    return gateType, output  # print( gate info  and output)


def main():
    OR_GATE_WEIGHT_AND_BIAS = {

        'OR_GET': {
            'w0': 0.3,
            'w1': 0.2

        },
        'bias': {
            'OR_GET': -0.13
        }
    }
    INPUT_VALUES = nmp.array( [
        user_iput
    ] )

    OR_GET = executePerceptron( 'OR_GET', OR_GATE_WEIGHT_AND_BIAS, INPUT_VALUES )

    def run(INPUT_VALUES, name, data):
        # act = name[6:]
        print("OR GATE NEURAL NET IMPLEMENTATION")
        print("X0\tX1\tOutput")
        result = ["{1}\t{2}\t{0}".format( output, *datas ) for datas, output in zip( INPUT_VALUES, data )]
        for i in result:
            print(i)

    gates = [OR_GET]

    for i in gates:
        run( INPUT_VALUES, *i )


if __name__ == '__main__':
    print("\nThe program allows entry all possible combinations of OR gate values with two iputs\n"
          "repeats process 8 to allow 4 possible combinations of X0 and X1\n"
          "x0 and x1 and gives output as either 0 or 1\nenter X0 and X1 as 0 or 1 \n\n"
          "start; key in after x0 and x1 below \n\n"
          "")
    for i in range( 8 ): # repeats process 8 to allow 4 possible combinations of x0 and x1
        n = input( "Enter  X" + str(x) + " " ) # 0 or 1 values
        user_iput.append( n )
        x = x + 1

        if i > 0 and i % 2 != 0:
            main()
            print("\n")
            user_iput = []
            x = 0
            continue
            
            
            
