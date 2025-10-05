# Docker debug
## Dev Contatiners
- Install Dev Containers in vscode extensions
- Connect to the docker image
- Run code below to activate dependencies (these can't be mapped)
``` bash
mv ${FINN_ROOT}/deps/qonnx/pyproject.toml ${FINN_ROOT}/deps/qonnx/pyproject.tmp
pip install --user -e ${FINN_ROOT}/deps/qonnx
mv ${FINN_ROOT}/deps/qonnx/pyproject.tmp ${FINN_ROOT}/deps/qonnx/pyproject.toml
# finn-experimental
pip install --user -e ${FINN_ROOT}/deps/finn-experimental
# brevitas
pip install --user -e ${FINN_ROOT}/deps/brevitas
# pyverilator
pip install --user -e ${FINN_ROOT}/deps/pyverilator
pip install --user -e ${FINN_ROOT}
```
- they are from docker/finn_entrypoint.sh