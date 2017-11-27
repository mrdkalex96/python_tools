
#!/usr/bin/env python

import hashlib
import optparse

# function that opens the wordlist and the hash file, then converts wordlist to hashes and finally checks if the hash file corresponds to $
def crack(dictionary,hashes,save):

    with open(dictionary,'r') as d:	   # opening wordlist
        dictio = d.readlines()             # saving content of file to dictio variable
    with open(hashes,'r') as p:            # opening hash file
        passwd = p.readlines()             # sasving content of file to passwd variable

    m = hashlib.md5()                      # instance of the md5 method 
    d = {}                                 # creating an empty dictionary
    for i in dictio:                       # iterating through the wordlist file
        m.update(i)                        # hashing the passwd
        d[m.hexdigest()] = i.rstrip('\n')  # adding in the dictionary
                                           # the key is the hashed passwd and the value is the password in plain test

    for pa in passwd:                      # iterating through the hash file
        if pa.rstrip('\n') in d:           # checking if any of these hash corresponds
            if len(save):                  # if save option is passed then saves to a file
                with open(save,'w') as o:
                    o.write('Password: '+pa)
            else:                          # otherwise just print it
                print 'Password Found',pa

def main():

    parser = optparse.OptionParser('usage '+ '-d <dictionary> -f <hash file> -s <destination file name>')   # usage
    parser.add_option('-d',dest='dictionary_name',type='string',help='enter the wordlist')                  # dictionary file
    parser.add_option('-f',dest='h_file',type='string',help='enter the passwd hashes file')                 # hash file
    parser.add_option('-s',dest='output',type='string',help='enter the name for the output file')           # output
    (options,args) = parser.parse_args()

    dictionary_name = options.dictionary_name   # assigning the cmd line option for wordlist to the variable --> dictionary/wordlist 
    hashes = options.h_file                     # assigning the cmd line option for hash file to the variable --> hashes file
    output = options.output                     # assigning the cmd line option for saving to the variable --> output file name, optional
    
    if (dictionary_name == None) | (hashes == None): # if no dictionary or no hash file print the usage
        print parser.usage
        exit(0)
    if (output == None):                     # if no file name is specified, the argument passed to the crack function is empty, so no fi$
        save = ''
    else:
	      save = output  

    crack(dictionary_name,hashes,save)      # calling crack function with dictionary file , hash file and output filename 


if __name__ == '__main__':
    main()


