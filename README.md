# Safe-Web-
Saas platform for cybersecurity . This Saas platform will detect, monitor  and prevent cyber threats. 





import { useState } from "react";
import { motion, AnimatePresence } from "framer-motion";
import { LineChart, Line, XAxis, YAxis, Tooltip, CartesianGrid } from "recharts";
import { Shield, AlertTriangle, BarChart2, Settings, Play } from "lucide-react";

const data = [
  { time: "10:00", threats: 2 },
  { time: "11:00", threats: 5 },
  { time: "12:00", threats: 3 },
  { time: "13:00", threats: 8 },
  { time: "14:00", threats: 4 },
];

export default function App() {
  const [sidebarOpen, setSidebarOpen] = useState(true);
  const [showModal, setShowModal] = useState(false);
  const [alerts, setAlerts] = useState([
    { id: 1, message: "Suspicious login attempt detected", severity: "High" },
    { id: 2, message: "Vulnerability found in port 443", severity: "Medium" },
    { id: 3, message: "Malware signature detected", severity: "Critical" },
  ]);

  const handleRunScan = (type) => {
    setShowModal(false);
    const newAlert = {
      id: alerts.length + 1,
      message: `${type} Scan completed. No critical issues.`,
      severity: type === "Full" ? "Info" : "Low",
    };
    setAlerts([newAlert, ...alerts]);
  };

  return (
    <div className="flex h-screen bg-gray-100">
      {/* Sidebar */}
      <aside className={`${sidebarOpen ? "w-64" : "w-16"} bg-blue-900 text-white transition-all duration-300 flex flex-col`}>
        <div className="flex items-center justify-between px-4 py-4">
          <span className={`font-bold text-xl ${sidebarOpen ? "block" : "hidden"}`}>SafeWeb</span>
          <button onClick={() => setSidebarOpen(!sidebarOpen)} className="text-white md:hidden">
            ☰
          </button>
        </div>
        <nav className="mt-6 flex-1">
          <ul>
            <li className="px-4 py-2 hover:bg-blue-700 flex items-center cursor-pointer">
              <Shield className="mr-3" /> {sidebarOpen && "Dashboard"}
            </li>
            <li className="px-4 py-2 hover:bg-blue-700 flex items-center cursor-pointer">
              <AlertTriangle className="mr-3" /> {sidebarOpen && "Alerts"}
            </li>
            <li className="px-4 py-2 hover:bg-blue-700 flex items-center cursor-pointer">
              <BarChart2 className="mr-3" /> {sidebarOpen && "Reports"}
            </li>
            <li className="px-4 py-2 hover:bg-blue-700 flex items-center cursor-pointer">
              <Settings className="mr-3" /> {sidebarOpen && "Settings"}
            </li>
          </ul>
        </nav>
      </aside>

      {/* Main Content */}
      <div className="flex-1 flex flex-col">
        {/* Topbar */}
        <header className="bg-white shadow px-6 py-4 flex justify-between items-center">
          <h1 className="text-2xl font-bold text-gray-800">Dashboard</h1>
          <div className="flex items-center gap-4">
            <button
              onClick={() => setShowModal(true)}
              className="flex items-center bg-blue-600 hover:bg-blue-700 text-white px-4 py-2 rounded shadow transition"
            >
              <Play className="mr-2 w-4 h-4" /> Run Scan
            </button>
            <span className="font-semibold">Admin</span>
            <img src="https://i.pravatar.cc/40" alt="avatar" className="rounded-full" />
          </div>
        </header>

        {/* Dashboard Content */}
        <main className="p-6 space-y-6 overflow-y-auto">
          {/* Cards */}
          <div className="grid grid-cols-1 md:grid-cols-3 gap-6">
            <motion.div whileHover={{ scale: 1.03 }} className="bg-white shadow-md rounded-lg p-4">
              <h2 className="text-lg font-semibold mb-2">Active Threats</h2>
              <p className="text-3xl font-bold text-red-600">12</p>
            </motion.div>

            <motion.div whileHover={{ scale: 1.03 }} className="bg-white shadow-md rounded-lg p-4">
              <h2 className="text-lg font-semibold mb-2">Vulnerabilities</h2>
              <p className="text-3xl font-bold text-yellow-500">8</p>
            </motion.div>

            <motion.div whileHover={{ scale: 1.03 }} className="bg-white shadow-md rounded-lg p-4">
              <h2 className="text-lg font-semibold mb-2">Resolved Issues</h2>
              <p className="text-3xl font-bold text-green-600">25</p>
            </motion.div>
          </div>

          {/* Chart + Alerts */}
          <div className="grid grid-cols-1 lg:grid-cols-2 gap-6">
            <div className="bg-white shadow-md rounded-lg p-6">
              <h2 className="text-xl font-semibold mb-4">Threat Activity</h2>
              <LineChart width={500} height={250} data={data}>
                <XAxis dataKey="time" />
                <YAxis />
                <Tooltip />
                <CartesianGrid stroke="#ccc" />
                <Line type="monotone" dataKey="threats" stroke="#2563eb" strokeWidth={2} />
              </LineChart>
            </div>

            <div className="bg-white shadow-md rounded-lg p-6 overflow-y-auto">
              <h2 className="text-xl font-semibold mb-4">Recent Alerts</h2>
              <ul className="space-y-2">
                {alerts.map((a) => (
                  <li key={a.id} className="p-3 border rounded flex justify-between items-center hover:bg-gray-50">
                    <span>{a.message}</span>
                    <span
                      className={`text-sm font-semibold px-2 py-1 rounded ${
                        a.severity === "Critical"
                          ? "bg-red-600 text-white"
                          : a.severity === "High"
                          ? "bg-orange-500 text-white"
                          : a.severity === "Medium"
                          ? "bg-yellow-400 text-black"
                          : "bg-blue-200 text-blue-800"
                      }`}
                    >
                      {a.severity}
                    </span>
                  </li>
                ))}
              </ul>
            </div>
          </div>
        </main>
      </div>

      {/* Scan Modal */}
      <AnimatePresence>
        {showModal && (
          <motion.div
            className="fixed inset-0 bg-black bg-opacity-50 flex items-center justify-center z-50"
            initial={{ opacity: 0 }}
            animate={{ opacity: 1 }}
            exit={{ opacity: 0 }}
          >
            <motion.div
              className="bg-white rounded-lg p-6 w-80 shadow-lg"
              initial={{ scale: 0.8 }}
              animate={{ scale: 1 }}
              exit={{ scale: 0.8 }}
            >
              <h2 className="text-xl font-bold mb-4">Run Security Scan</h2>
              <p className="text-gray-600 mb-4">Choose the type of scan to run:</p>
              <div className="space-y-2">
                <button
                  onClick={() => handleRunScan("Quick")}
                  className="w-full bg-blue-600 text-white py-2 rounded hover:bg-blue-700 transition"
                >
                  Quick Scan
                </button>
                <button
                  onClick={() => handleRunScan("Full")}
                  className="w-full bg-gray-700 text-white py-2 rounded hover:bg-gray-800 transition"
                >
                  Full Scan
                </button>
              </div>
              <button
                onClick={() => setShowModal(false)}
                className="mt-4 w-full bg-red-500 text-white py-2 rounded hover:bg-red-600 transition"
              >
                Cancel
              </button>
            </motion.div>
          </motion.div>
        )}
      </AnimatePresence>
    </div>
  );
}