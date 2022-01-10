from glob import glob
from pathlib import Path
import subprocess
import os
import platform
import psutil

if platform.system() == 'Windows':
    proc = psutil.Process(os.getpid())
    proc.nice(psutil.HIGH_PRIORITY_CLASS)

base_convert_dir = 'convert-out'

base_convert_path = Path(base_convert_dir)
files = glob('**/*.mp4')

for f in files:
    new_path = base_convert_path.joinpath(f)
    new_file = str(new_path)

    if new_path.exists():
        print('exists, skipping {0}'.format(new_file))
        continue

    print('converting {0}'.format(f))
    subprocess.run('ffmpeg -i {0} {1}'.format(f, new_file))
    print('saved to {0}'.format(new_file))
