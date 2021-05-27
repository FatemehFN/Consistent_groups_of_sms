## consistent_groups_of_sms
 
This algorithm generates the consistent groups of stable motifs and conditionally stable motifs in plant-pollinator interaction networks. Once those groups are identified, the code finds the ones that mutually exclude each other. These groups lead to distict new attractors. The algorithm is described in the following article:



## I) Notations:

The function `form_network()` from the module `BooleanDOI_processing` reads the Boolean functions from a text file and constructs the network accordingly. The network is stored in a networkx DiGraph object. This function assigns a new name in the format of *n*+ a number + *n* to each node.


Example

pl_1*=po_1
po_1*=pl_1

original notation          number index
        pl_1                    n1n
        po_1                    n2n



The network that is constructed from the text file of the Boolean functions is in 'number index' notation
The expanded network is in 'number index' notation
The LDOI operations are in 'number index' notation
The output of PyBoolNet is in the original notation, which is pl-po in plant-pollinator networks 
The stable motifs generated by the PyBoolNet trap_spaces() is in the pl-po notation. Example: [{pl_0:0, po_1:0},{pl_0:1, po_1:1}]
The names of nodes in network of functional relationships is in pl-po notation



mapping provides this information from the node names (original notation) to number index notation. 
reverse mapping provides the mapping from the number index notation to node names (original notation)

Consistent cycles and conditionally stable motifs are stored in this format: [{'n1': 0, 'n2': 0}, {'~n3', '~n0'}]. 

The first item is a dictionary of nodes and their states in that consistent cycle/consitionally stable motif, and the second item is a set of conditions with '~' showing the inactive state. It is stored in this format so that it would be easier to check if this set is a subset of LDOI of a set of node states. 



# II) Instructions

There are several python files with examples. 


File example_1.py demostrates generation of disjunctive prime form and simplified Boolean models for plant pollinator networks in text files. There are several inputs that can be provided if necessary: perturb, wp, IC, write_IC. These inputs provide the option of having initial conditions or/and perturbation in the Boolean model written in the text files. Functions disjunctive_prime_form_text_file() and simplification_text_file() write the Boolean functions in text files. 


File example_2.py demonstrates how one can use the funtion cycle_graph_virtual_node_based() to construct the cycle graph. The Boolean functions should be read from a text file using fundtion readlines() and this is the only argument to this function. It writes the cycle graph in a gml file that can be opened by YED. 

Files example_3.py has an example of code execution for a plant pollinator network model. First the network of functional relationships should be constructed using the function construct_relationships_network(). Then that network should be provided for the consistent_groups_of_sms() function as an argument. This function finds the consistent groups of stable motifs and conditionally stable motifs that are mutually exclusive. It returns the number of attractors and the list of these mutually exclusive groups. 
        
File example_4.py executes the same code for plant-pollinator like network models.


# III) software used 
