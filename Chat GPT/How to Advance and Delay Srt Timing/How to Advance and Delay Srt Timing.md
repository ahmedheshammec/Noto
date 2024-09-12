we will use python script for that 
Delay Script: 
```plaintext
def delay_srt_timing(input_file, output_file):
with open(input_file, 'r') as infile:
 lines = infile.readlines()

with open(output_file, 'w') as outfile:
for line in lines:
if'-->'in line:
 start_time, end_time = line.strip().split(' --> ')
 start_time_parts = start_time.split(':')
 end_time_parts = end_time.split(':')

 start_seconds = int(start_time_parts[0]) * 3600 + int(start_time_parts[1]) * 60 + float(start_time_parts[2].replace(',', '.'))
 end_seconds = int(end_time_parts[0]) * 3600 + int(end_time_parts[1]) * 60 + float(end_time_parts[2].replace(',', '.'))

 new_start_seconds = start_seconds + 1# Delay timing by 1 second
 new_end_seconds = end_seconds + 1# Delay timing by 1 second

 new_start_time = '{:02}:{:02}:{:.03f}'.format(
 int(new_start_seconds // 3600),
 int((new_start_seconds % 3600) // 60),
 new_start_seconds % 60
 )

 new_end_time = '{:02}:{:02}:{:.03f}'.format(
 int(new_end_seconds // 3600),
 int((new_end_seconds % 3600) // 60),
 new_end_seconds % 60
 )

 outfile.write("{0} --> {1}\n".format(new_start_time.replace('.', ','), new_end_time.replace('.', ',')))
else:
 outfile.write(line)

if __name__ == "__main__":
 input_file = "input.srt"# Replace with your input SRT file
 output_file = "output.srt"# Replace with the desired output file name
 delay_srt_timing(input_file, output_file)
 print("Subtitles delayed by 1 second. Modified subtitles saved to '{0}'".format(output_file))


```
and here's the advance srt script: 
```plaintext
def advance_srt_timing(input_file, output_file):
with open(input_file, 'r') as infile:
 lines = infile.readlines()

with open(output_file, 'w') as outfile:
for line in lines:
if'-->'in line:
 start_time, end_time = line.strip().split(' --> ')
 start_time_parts = start_time.split(':')
 end_time_parts = end_time.split(':')

 start_seconds = int(start_time_parts[0]) * 3600 + int(start_time_parts[1]) * 60 + float(start_time_parts[2].replace(',', '.'))
 end_seconds = int(end_time_parts[0]) * 3600 + int(end_time_parts[1]) * 60 + float(end_time_parts[2].replace(',', '.'))

 new_start_seconds = start_seconds - 1# Advance timing by 1 second
 new_end_seconds = end_seconds - 1# Advance timing by 1 second

 new_start_time = '{:02}:{:02}:{:.03f}'.format(
 int(new_start_seconds // 3600),
 int((new_start_seconds % 3600) // 60),
 new_start_seconds % 60
 )

 new_end_time = '{:02}:{:02}:{:.03f}'.format(
 int(new_end_seconds // 3600),
 int((new_end_seconds % 3600) // 60),
 new_end_seconds % 60
 )

 outfile.write("{0} --> {1}\n".format(new_start_time.replace('.', ','), new_end_time.replace('.', ',')))
else:
 outfile.write(line)

if __name__ == "__main__":
 input_file = "input.srt"# Replace with your input SRT file
 output_file = "output.srt"# Replace with the desired output file name
 advance_srt_timing(input_file, output_file)
 print("Subtitles advanced by 1 second. Modified subtitles saved to '{0}'".format(output_file))


```
This modified script should work without any issues on Python versions earlier than Python 3.6. You can replace "input.srt" with the filename of your input SRT file and specify the desired output file name as "output.srt" or any other name you prefer.

