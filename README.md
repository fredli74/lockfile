# lockfile #

Package lockfile implements a simple automatic lockfile (PID) method for golang.


    func Lock(name string) (*LockFile, error)

Lock automatically checks if the file already exists, if so, reads the process ID from the file and checks if the process is running. If the process is running a nil lock is returned and an error stating "Locked by other process".

    func (l *LockFile) Unlock()

Unlock closes and deletes the lock file previously created by Lock()


### Example ###
```
#!go

		if lock, err := lockfile.Lock(filename); err != nil {
			panic(err)
		} else {
			defer lock.Unlock()
		}
```