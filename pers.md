PERSISTENT STORAGE:
	
   Storage:
	
	Computer data storage, often called storage or memory, is a technology consisting of computer components and recording media used to retain digital data. It is a core function and fundamental component of computers.
	Historically, memory has been called core, main memory, real storage or internal memory. Meanwhile, non-volatile storage devices have been referred to as secondary storage, external memory or auxiliary/peripheral storage.
 
    #Persistent Storage:
 
	Persistent storage is any data storage device that retains data after power to that device is shut off. It is also sometimes referred to as non-volatile storage.

        In python,

          Data Persistence:

        	“Pickling” is the process whereby a Python object hierarchy is converted into a byte stream, and “unpickling” is the inverse operation, whereby a byte stream is converted back into an object hierarchy.

                Pickle: Python has a more primitive serialization module called marshal, but in general pickle should always be the preferred way to serialize Python objects. marshal exists primarily to support Python’s .pyc files.

                cPickle: The cPickle module supports serialization and de-serialization of Python objects, providing an interface and functionality nearly identical to the pickle module. There are several differences, the most important being performance and subclassability.

                      cPickle can be up to 1000 times faster than pickle because the former is implemented in C.
                      In the cPickle module the callables Pickler() and Unpickler() are functions, not classes. This means that you cannot use them to derive custom pickling and unpickling subclasses.

                copy_reg: The copy_reg module offers a way to define functions used while pickling specific objects. The pickle, cPickle, and copy modules use those functions when pickling/copying those objects. The module provides configuration information about object constructors which are not classes. Such constructors may be factory functions or class instances.

          Object Persistence:

	          #Shelve:

                      A “shelf” is a persistent.the values (not the keys!) in a shelf can be essentially arbitrary Python objects — anything that the pickle module can handle. This includes most class instances, recursive data types, and objects containing lots of shared sub-objects. The keys are ordinary strings.

                        shelve.open(filename, flag='c', protocol=None, writeback=False)

                  #Masrshal:

                      The marshal module exists mainly to support reading and writing the “pseudo-compiled” code for Python modules of .pyc files.
                      The module defines these functions:

                         marshal.dump(value, file[, version])
                      It write the value on the open file. The value must be a supported type. 
                         marshal.load(file)
                      Read one value from the open file and return it. If no valid value is read raise an error.

                  #anydbm:

 		      anydbm is a generic interface to variants of the DBM database — dbhash (requires bsddb), gdbm, or dbm. If none of these modules is installed, the slow-but-simple implementation in module dumbdbm will be used.

                         anydbm.open(filename[, flag[, mode]])
                      Open the database file filename and return a corresponding object.

                      If the database file already exists, the whichdb module is used to determine its type and the appropriate module is used; if it does not exist, the first module listed above that can be imported is used.

                  #dumbdbm:

                      The dumbdbm module provides a persistent dictionary-like interface which is written entirely in Python. Unlike other modules such as gdbm and bsddb, no external library is required. As with other persistent mappings, the keys and values must always be strings.

                      The module defines the following:

                           exception dumbdbm.error

                        Raised on dumbdbm-specific errors, such as I/O errors. KeyError is raised for general mapping errors like specifying an incorrect key.

                           dumbdbm.open(filename[, flag[, mode]])

                        Open a dumbdbm database and return a dumbdbm object. The filename argument is the basename of the database file (without any specific extensions). When a dumbdbm database is created, files with .dat and .dir extensions are created.

                           dumbdbm.close()
                        Close the dumbdm database.


