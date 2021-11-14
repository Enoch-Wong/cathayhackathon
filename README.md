# cathayhackathon
def budget(destinations, minbudget, maxbudget, overall):
    budget = input().split()
    minbudget = []
    maxbudget = []
    while (budget[0] != 'END'):
        name = budget[0]

        for i in budget[1:2]:
            minbudget.append(int(i))
            #print(minbudget)
        for j in budget[2:3]:
            maxbudget.append(int(j))
            #print(maxbudget)
        budget = input().split()
    
    minbudget.sort()
    maxbudget.sort()
    #print(minbudget)
    #print(maxbudget)
    overall = []
    overall.append(minbudget[0])
    overall.append(maxbudget[0])
    #print(overall)
    #return overall
    def criteria(destinations, A, B, overall):
        #print(overall)
        for i in range(len(destinations[A])):
            integer = int(destinations[A][i])
            if integer in range(overall[0], overall[1]):
                return False
        for i in range(len(destinations[A])):
            if integer not in range(overall[0], overall[1]):
                return True
        return False

    def finaldestination(destinations, overall):
        result = []
        for i in destinations:
            appendI = True
            for j in destinations:
                if i == j:
                    continue
                if (i!=j and criteria(destinations, i, j, overall)):
                    appendI = False
                    break
            if appendI == True:
                result.append(i)
        
        #print(result)
        return result
    
    print(finaldestination(destinations, overall))

def read_destinations(destinations):
    command = input().split()
    while (command[0] != 'END'):
        name = command[0]

        destinations[name] = []
        for i in command[1:]:
            destinations[name].append(int(i))
        command = input().split()
    
    #print(destinations)
    #return(destinations)




def main():
    destinations = {}
    read_destinations(destinations)
    minbudget = {}
    maxbudget = {}
    overall = {}
    budget(destinations, minbudget, maxbudget, overall)
    #print(budget)
    #print(finaldestination(destinations, overall))

main()
