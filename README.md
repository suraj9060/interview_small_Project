# stop watch logic
function App() {
  const [time, setTime] = useState(0);
  const [status, setStatus] = useState(false);

  useEffect(() => {
    let interval = null;
    if (status) {
      interval = setInterval(() => {
        setTime((PrivTime) => PrivTime + 10);
      }, 10);
    } else {
      clearInterval(interval);
    }

    return () => clearInterval(interval);
  }, [status]);

  return (
    <div className="App">
      <h2>
        <span>{("0" + Math.floor((time / 60000) % 60)).slice(-2)}</span>:
        <span>{("0" + Math.floor((time / 1000) % 60)).slice(-2)}</span>:
        <span>{("0" + ((time / 10) % 100)).slice(-2)}</span>
      </h2>
      <button onClick={() => setStatus(true)}>start</button>
      <button onClick={() => setStatus(false)}>stop</button>
      <button onClick={() => setStatus(true)}>resume</button>
      <button onClick={() => setTime(0)}>reset</button>
    </div>
  );
}
