# MIT Membrane Impedance Tube

LabVIEW projects for a membrane impedance tube measurement system, including
2-microphone and 4-microphone related workflows, calibration utilities, and
LabVIEW application build specifications.

本仓库用于保存阻抗管测试系统的 LabVIEW 源程序，包括主测量程序、单独校准程序以及麦克风校准数据。

## Repository Structure

| Path | Description |
| --- | --- |
| `10Kimp_tube Folder_Labview2018/` | LabVIEW 2018 version of the 10 kHz impedance tube project. |
| `阻抗管0318_labview2021/` | LabVIEW 2021 version of the impedance tube project, including calibration text files. |
| `README.md` | Project overview and usage notes. |

Inside each LabVIEW project folder:

| File | Purpose |
| --- | --- |
| `10Kimp_tube.lvproj` | Main LabVIEW project for the impedance tube measurement application. |
| `10K阻抗管318.vi` | Top-level VI for the main measurement program. |
| `cal_only.lvproj` | Standalone calibration project. |
| `校准专用.vi` | Top-level VI for calibration-only operation. |
| `*.aliases` | LabVIEW target aliases. The LabVIEW 2018 folder currently points to `192.168.2.168`. |
| `*.lvlps` | LabVIEW local project settings and build-cache metadata. |

The LabVIEW 2021 folder also contains `！校准/` calibration data files such as
`mic1校准.txt` through `mic4校准.txt`.

## Software Requirements

- NI LabVIEW 2018 for `10Kimp_tube Folder_Labview2018/`
- NI LabVIEW 2021 for `阻抗管0318_labview2021/`
- NI-DAQmx / NI-DAQmx Runtime 22.5
- NI Sound and Vibration related libraries used by the projects
- Windows environment compatible with the selected LabVIEW runtime

Do not save the project in a newer LabVIEW version unless the target deployment
environment has also been upgraded.

## Hardware Notes

The applications use NI-DAQmx analog input/output functionality and are intended
for an impedance-tube test setup. Before running the VIs, confirm that:

1. The NI DAQ device is connected and visible in NI MAX.
2. Channel names and sensor settings in the VIs match the actual test hardware.
3. Microphone or sensor calibration has been completed with the calibration VI.
4. The LabVIEW target alias/IP is correct for the current host or target.

## Running from LabVIEW

### Main Measurement Program

1. Open the required LabVIEW version folder.
2. Open `10Kimp_tube.lvproj`.
3. Open `10K阻抗管318.vi`.
4. Check DAQ channel configuration, sampling parameters, signal-generation
   settings, calibration files, and save paths.
5. Run the VI from LabVIEW.

### Calibration Program

1. Open the required LabVIEW version folder.
2. Open `cal_only.lvproj`.
3. Open `校准专用.vi`.
4. Configure the calibration hardware and acquisition channels.
5. Run the VI and save/update the calibration data required by the measurement
   workflow.

## Building Applications

The LabVIEW 2018 projects include these build specifications:

| Project | Build Specification | Output |
| --- | --- | --- |
| `10Kimp_tube.lvproj` | `10K_imp_tube` | `10K_imp_tube.exe` |
| `10Kimp_tube.lvproj` | `My Installer1` | `install.exe` for `10Kimp_tube` |
| `cal_only.lvproj` | `cal_only` | `cal_only.exe` |
| `cal_only.lvproj` | `My Installer2` | `install.exe` for `cal_only` |

Expected build output folders are under `builds/`. Generated build products are
not tracked in this repository.

## Version-Control Notes

- LabVIEW binary files such as `.vi` are tracked as binary files.
- Generated build outputs, LabVIEW build caches, autosave files, and local
  temporary files should be excluded from commits.
- If the test hardware, NI runtime version, calibration data, or target IP
  changes, update the corresponding LabVIEW project/VI settings before
  rebuilding or running tests.

## License

No license has been specified yet.
