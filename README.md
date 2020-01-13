# Python2Simulink
A bridge between Python and Simulink
This file aims to Call Simulink module with Python.

## Install MATLAB Engine API for Python

Install the MATLAB Engine API follow the instruction [Installation](https://www.mathworks.com/help/matlab/matlab_external/install-the-matlab-engine-for-python.html).

## Applications
1. plant example
2. tracking example


## API
- start the engine and connect to Matlab; Load the model:

`matlab.engine.start_matlab()`

`self.eng.eval("model = '{}'".format(self.modelName),nargout=0)`

`self.eng.eval("load_system(model)",nargout=0)`

- eng.eval('out.output')

- eng.workspace()

- self.eng.set_param('{}/u'.format(self.modelName),'value',str(u),nargout=0): set the control input u.

- Start Simulation and then Instantly pause and read output.

```
eng.set_param(self.modelName,'SimulationCommand','start','SimulationCommand','pause',nargout=0)
out = self.eng.workspace['out']
self.eng.eval('out.output'), self.eng.eval('out.tout')
```


## Reference:
1. [link1](https://stackoverflow.com/questions/48864281/executing-step-by-step-a-simulink-model-from-python)
2. [Calling MATLAB from Python](https://www.mathworks.com/help/matlab/matlab-engine-for-python.html)
3. [Troubleshoot MATLAB Errors in Python](https://www.mathworks.com/help/matlab/matlab_external/troubleshoot-matlab-errors-in-python.html)