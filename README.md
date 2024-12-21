import React, { useState, useEffect } from 'react';
import { LayoutGrid, Code2, Rocket, Music, Trophy } from 'lucide-react';
import { Card, CardContent } from '@/components/ui/card';

const FourDProfile = () => {
  const [activeTab, setActiveTab] = useState('about');
  const [rotateY, setRotateY] = useState(0);

  useEffect(() => {
    const interval = setInterval(() => {
      setRotateY(prev => (prev + 1) % 360);
    }, 50);
    return () => clearInterval(interval);
  }, []);

  const tabStyle = (tab) => `
    ${activeTab === tab ? 'bg-gradient-to-r from-purple-600 to-pink-600 text-white' : 'bg-gray-800 text-gray-300'}
    px-4 py-2 rounded-lg cursor-pointer hover:opacity-90 transition-all
  `;

  return (
    <div className="w-full max-w-4xl mx-auto p-6 bg-gray-900 rounded-2xl shadow-2xl">
      {/* Header Section */}
      <div className="relative mb-8">
        <div className="absolute inset-0 bg-gradient-to-r from-purple-600 via-pink-600 to-blue-600 rounded-lg opacity-20 animate-pulse"></div>
        <div className="relative p-6 text-center">
          <h1 className="text-4xl font-bold bg-clip-text text-transparent bg-gradient-to-r from-purple-400 to-pink-600">
            Chretien Banza
          </h1>
          <p className="text-gray-400 mt-2">Co-Founder @DrawFi • Sandbox Innovator</p>
        </div>
      </div>

      {/* Navigation Tabs */}
      <div className="flex gap-4 mb-6 overflow-x-auto">
        {[
          { id: 'about', icon: <LayoutGrid size={20} />, label: 'Profile' },
          { id: 'skills', icon: <Code2 size={20} />, label: 'Tech' },
          { id: 'projects', icon: <Rocket size={20} />, label: 'Ventures' },
          { id: 'achievements', icon: <Trophy size={20} />, label: 'Achievements' },
          { id: 'music', icon: <Music size={20} />, label: 'Music' }
        ].map(tab => (
          <button
            key={tab.id}
            onClick={() => setActiveTab(tab.id)}
            className={tabStyle(tab.id)}
          >
            <div className="flex items-center gap-2">
              {tab.icon}
              <span>{tab.label}</span>
            </div>
          </button>
        ))}
      </div>

      {/* Main Content Area */}
      <div className="relative perspective-1000">
        <div 
          className="transform-gpu transition-transform duration-500"
          style={{ transform: `rotateY(${activeTab === 'about' ? rotateY : 0}deg)` }}
        >
          {activeTab === 'about' && (
            <Card className="bg-gray-800 border-0">
              <CardContent className="p-6">
                <div className="grid grid-cols-2 gap-4">
                  <div className="space-y-4">
                    <div className="relative p-4 bg-gray-700 rounded-lg overflow-hidden">
                      <div className="absolute inset-0 bg-gradient-to-r from-purple-600 to-pink-600 opacity-10"></div>
                      <h3 className="text-xl font-bold text-white mb-2">DrawFi Co-Founder</h3>
                      <p className="text-gray-300">Leading innovation in construction lending</p>
                    </div>
                    <div className="relative p-4 bg-gray-700 rounded-lg overflow-hidden">
                      <div className="absolute inset-0 bg-gradient-to-r from-blue-600 to-purple-600 opacity-10"></div>
                      <h3 className="text-xl font-bold text-white mb-2">Sandbox Elite</h3>
                      <p className="text-gray-300">Startup school innovator</p>
                    </div>
                  </div>
                  <div className="space-y-4">
                    <div className="relative p-4 bg-gray-700 rounded-lg overflow-hidden">
                      <div className="absolute inset-0 bg-gradient-to-r from-pink-600 to-purple-600 opacity-10"></div>
                      <h3 className="text-xl font-bold text-white mb-2">Tech Visionary</h3>
                      <p className="text-gray-300">Full stack development expert</p>
                    </div>
                    <div className="relative p-4 bg-gray-700 rounded-lg overflow-hidden">
                      <div className="absolute inset-0 bg-gradient-to-r from-purple-600 to-blue-600 opacity-10"></div>
                      <h3 className="text-xl font-bold text-white mb-2">Musical Artist</h3>
                      <p className="text-gray-300">Multi-instrumentalist & creator</p>
                    </div>
                  </div>
                </div>
              </CardContent>
            </Card>
          )}

          {activeTab === 'skills' && (
            <Card className="bg-gray-800 border-0">
              <CardContent className="p-6">
                <div className="grid grid-cols-1 md:grid-cols-2 gap-4">
                  {[
                    { name: 'Python', level: 95 },
                    { name: 'React', level: 90 },
                    { name: 'Flutter', level: 88 },
                    { name: 'Django', level: 92 }
                  ].map(skill => (
                    <div key={skill.name} className="relative p-4 bg-gray-700 rounded-lg">
                      <div className="flex justify-between mb-2">
                        <span className="text-white">{skill.name}</span>
                        <span className="text-gray-400">{skill.level}%</span>
                      </div>
                      <div className="h-2 bg-gray-600 rounded-full overflow-hidden">
                        <div 
                          className="h-full bg-gradient-to-r from-purple-600 to-pink-600"
                          style={{ width: `${skill.level}%` }}
                        />
                      </div>
                    </div>
                  ))}
                </div>
              </CardContent>
            </Card>
          )}

          {activeTab === 'projects' && (
            <Card className="bg-gray-800 border-0">
              <CardContent className="p-6">
                <div className="grid grid-cols-1 md:grid-cols-2 gap-4">
                  {[
                    {
                      name: 'DrawFi',
                      description: 'Construction lending platform',
                      color: 'from-purple-600 to-pink-600'
                    },
                    {
                      name: 'wrkbnch',
                      description: 'Contractor operations platform',
                      color: 'from-blue-600 to-purple-600'
                    },
                    {
                      name: 'SmartyKids',
                      description: 'Educational gaming platform',
                      color: 'from-pink-600 to-purple-600'
                    },
                    {
                      name: 'SoundGrid',
                      description: 'Music collaboration platform',
                      color: 'from-purple-600 to-blue-600'
                    }
                  ].map(project => (
                    <div key={project.name} className="relative p-4 bg-gray-700 rounded-lg overflow-hidden">
                      <div className={`absolute inset-0 bg-gradient-to-r ${project.color} opacity-10`}></div>
                      <h3 className="text-xl font-bold text-white mb-2">{project.name}</h3>
                      <p className="text-gray-300">{project.description}</p>
                    </div>
                  ))}
                </div>
              </CardContent>
            </Card>
          )}

          {activeTab === 'achievements' && (
            <Card className="bg-gray-800 border-0">
              <CardContent className="p-6">
                <div className="space-y-4">
                  {[
                    'DrawFi Co-Founder & Launch',
                    'Sandbox Hackathon Winner',
                    'Stanford UIF Program',
                    'Multi-Instrument Mastery'
                  ].map((achievement, index) => (
                    <div key={index} className="relative p-4 bg-gray-700 rounded-lg overflow-hidden">
                      <div className="absolute inset-0 bg-gradient-to-r from-purple-600 to-pink-600 opacity-10"></div>
                      <div className="flex items-center gap-3">
                        <Trophy className="text-yellow-500" size={24} />
                        <span className="text-white">{achievement}</span>
                      </div>
                    </div>
                  ))}
                </div>
              </CardContent>
            </Card>
          )}

          {activeTab === 'music' && (
            <Card className="bg-gray-800 border-0">
              <CardContent className="p-6">
                <div className="text-center space-y-4">
                  <Music size={48} className="mx-auto text-purple-500" />
                  <h3 className="text-xl font-bold text-white">Musical Journey</h3>
                  <p className="text-gray-300">Proficient in 5+ instruments including:</p>
                  <div className="grid grid-cols-2 gap-4 mt-4">
                    {['Piano 🎹', 'Guitar 🎸', 'Drums 🥁', 'Bass 🎸', 'Synthesizer 🎹'].map((instrument, index) => (
                      <div key={index} className="p-3 bg-gray-700 rounded-lg text-white">
                        {instrument}
                      </div>
                    ))}
                  </div>
                </div>
              </CardContent>
            </Card>
          )}
        </div>
      </div>
    </div>
  );
};

export default FourDProfile;
