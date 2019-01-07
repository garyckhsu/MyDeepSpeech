# MyDeepSpeech
deep search based on Mozilla Deep Search (https://github.com/mozilla/DeepSpeech)

# Prerequisites
see https://github.com/mozilla/DeepSpeech#prerequisites

# Using python package
test step:
1. virtualenv -p python3 /Users/garyhsu/workspace/deepspeech-venv
2. source /Users/garyhsu/workspace/deepspeech-venv/bin/activate
3. using pre-train model 
4. deepspeech --model output_graph.pbmm --alphabet alphabet.txt --lm lm.binary --trie trie --audio OSR_us_000_0010_8k.wav
Loading model from file output_graph.pbmm

Result:
[https://github.com/garyckhsu/MyDeepSpeech/blob/master/test_result.jpg](https://github.com/garyckhsu/MyDeepSpeech/blob/master/test_result.jpg)

test dataset:
http://www.voiptroubleshooter.com/open_speech/index.html

# Trouble shooting

# issue 
deepspeech --model output_graph.pbmm --alphabet alphabet.txt --lm lm.binary --trie trie --audio OSR_us_000_0010_8k.wav
Loading model from file output_graph.pbmm
TensorFlow: v1.11.0-9-g97d851f04e
DeepSpeech: unknown
2019-01-04 15:53:42.471941: I tensorflow/core/platform/cpu_feature_guard.cc:141] Your CPU supports instructions that this TensorFlow binary was not compiled to use: AVX2 FMA
Loaded model in 0.00663s.
Loading language model from files lm.binary trie
Loaded language model in 5.36s.
Warning: original sample rate (8000) is different than 16kHz. Resampling might produce erratic speech recognition.
Traceback (most recent call last):
  File "/Users/garyhsu/workspace/deepspeech-venv/lib/python3.6/site-packages/deepspeech/client.py", line 46, in convert_samplerate
    output = subprocess.check_output(shlex.split(sox_cmd), stderr=subprocess.PIPE)
  File "/Library/Frameworks/Python.framework/Versions/3.6/lib/python3.6/subprocess.py", line 336, in check_output
    **kwargs).stdout
  File "/Library/Frameworks/Python.framework/Versions/3.6/lib/python3.6/subprocess.py", line 403, in run
    with Popen(*popenargs, **kwargs) as process:
  File "/Library/Frameworks/Python.framework/Versions/3.6/lib/python3.6/subprocess.py", line 709, in __init__
    restore_signals, start_new_session)
  File "/Library/Frameworks/Python.framework/Versions/3.6/lib/python3.6/subprocess.py", line 1344, in _execute_child
    raise child_exception_type(errno_num, err_msg, err_filename)
FileNotFoundError: [Errno 2] No such file or directory: 'sox': 'sox'

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/Users/garyhsu/workspace/deepspeech-venv/bin/deepspeech", line 11, in <module>
    sys.exit(main())
  File "/Users/garyhsu/workspace/deepspeech-venv/lib/python3.6/site-packages/deepspeech/client.py", line 97, in main
    fs, audio = convert_samplerate(args.audio)
  File "/Users/garyhsu/workspace/deepspeech-venv/lib/python3.6/site-packages/deepspeech/client.py", line 50, in convert_samplerate
    raise OSError(e.errno, 'SoX not found, use 16kHz files or install it: {}'.format(e.strerror))
FileNotFoundError: [Errno 2] SoX not found, use 16kHz files or install it: No such file or directory: 'sox'
  
# Solution
$brew install sox

