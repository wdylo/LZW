
-------------------------Lempel–Ziv–Welch (LZW) algorithm Implementation-----------------------------------------------------------


# About
-----

The Lempel–Ziv–Welch (LZW) algorithm is a lossless data compression algorithm. LZW is an adaptive compression algorithm that does not assume prior knowledge of the input data distribution. This algorithm executes well when the input data is sufficiently large and have redundancy in the data.

Encoder and Decoder are LZW compression alogorithm programs in Java.


# Encoder Pseudocode Used:
------------------------

MAX_TABLE_SIZE=2(bit_length) //bit_length is number of encoding bits
initialize TABLE[0 to 255] = code for individual characters
STRING = null
while there are still input symbols:
	SYMBOL = get input symbol
	if STRING + SYMBOL is in TABLE:
		STRING = STRING + SYMBOL
	else:
		output the code for STRING
		If TABLE.size < MAX_TABLE_SIZE: // if table is not full
			add STRING + SYMBOL to TABLE // STRING + SYMBOL now has a code
	STRING = SYMBOL
output the code for STRING



# Decoder Pseudocode Used:
------------------------

MAX_TABLE_SIZE=2(bit_length)
initialize TABLE[0 to 255] = code for individual characters
CODE = read next code from encoder
STRING = TABLE[CODE]
output STRING
	while there are still codes to receive:
		CODE = read next code from encoder
		if TABLE[CODE] is not defined: // needed because sometimes the
			NEW_STRING = STRING + STRING[0] // decoder may not yet have code!
		else:
			NEW_STRING = TABLE[CODE]
		output NEW_STRING
		if TABLE.size < MAX_TABLE_SIZE:
			add STRING + NEW_STRING[0] to TABLE
		STRING = NEW_STRING


# Build / Compile the program
---------------------------

Make sure java(i.e jdk1.8) is installed in the system, before build the class.

Two arguments are passed while bulding the class

javac filename.java

Once the above command is executed, filename.class file is created


# Run the Program
---------------
Two arguments are passed to the class file as below.

1. InputfileName - The file which is used to compress.
2. Bitlength - The length that is to be used in the program. 

(Note: BitLength should be 8 to 16 as per the program requirements)


java filename InputfileName Bitlength


# Program Descriptions
----------------------

Programming language used : JAVA

Compiler Version: 1.8

* The HasMap Datastructure is used to create the table which hold the ASCII characters and their values.
	
	Syntax:
	-------

	Map<String, Integer> TABLE = new HashMap<String, Integer>();

* BufferedReader and BufferedWriter are used to read and write the files.

*IOException is thrown, for Input/Outputs that is available during the run time of the program.

To encode the input file, encoder.java file is used to create the compression file.

To decode the compression file, decoder.java is used to create decoded input file.

The compression file that is encoded by encoder class will pass to the decoder as input.

The compression file, which is created using UTF_16BE, will be saved in 16-bit format.

	Encoder.java
	------------

	This has two methods:
	
	1.Encode_string() which is used to create the table and the encoded text followed the pseudocode.

	2.CreateLZWfile() which is used to get the encoded text and create the compression file in a 16-bit format.

	Decoder.java
	------------

	This has two methods:
	
	1.Decode_String() which is used to create the table and decipher the decoded text followed the pseudocode.

	2.Create_decoded_file() which is used to get the decoded text and create the decoded file.



# What works well?
----------------

The Encoder program produces the compressed file in a 16bit format.
The Decoder program converts the compressed file back to the original input file. i.e Decoded text file.








