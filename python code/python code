# Iterate through each state in the DFA
for in_state in q:
    # Iterate through each symbol in the DFA alphabet
    for symbol in dfa_letters:
        # If the current state has only one element and there is a valid transition in the NFA
        if len(in_state) == 1 and (in_state[0], symbol) in nfa_transitions:
            # Set the DFA transition for the current state and symbol to the NFA transition
            dfa_transitions[(in_state, symbol)] = nfa_transitions[(in_state[0], symbol)]

            # If the destination state is not already in the DFA states, add it
            if tuple(dfa_transitions[(in_state, symbol)]) not in q:
                q.append(tuple(dfa_transitions[(in_state, symbol)]))
        else:
            # If the current state has more than one element, or there is no direct NFA transition
            dest = []     # Initialize a list to store destination states
            f_dest = []   # Initialize a list to store final destination states without duplicates

            # Iterate through each state in the current state
            for n_state in in_state:
                # Check if there is a valid NFA transition for the current state and symbol
                if (n_state, symbol) in nfa_transitions and nfa_transitions[(n_state, symbol)] not in dest:
                    # Add the destination state to the list
                    dest.append(nfa_transitions[(n_state, symbol)])

            # If there are destination states
            if dest:
                # Iterate through each destination state in the list
                for d in dest:
                    # Iterate through each value in the destination state
                    for value in d:
                        # Add the value to the final destination state list without duplicates
                        if value not in f_dest:
                            f_dest.append(value)

                # Set the DFA transition for the current state and symbol to the final destination states
                dfa_transitions[(in_state, symbol)] = f_dest

                # If the final destination state is not already in the DFA states, add it
                if tuple(f_dest) not in q:
                    q.append(tuple(f_dest)
