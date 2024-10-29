import React, { useState } from 'react';
import { Github, Linkedin, Mail, ExternalLink, Server, Cloud, Database, Code } from 'lucide-react';

const Portfolio = () => {
  const [activeTab, setActiveTab] = useState('projects');

  const projects = [
    {
      title: "Cloud Infrastructure Automation",
      description: "Developed infrastructure as code using Ansible to automate deployment of microservices across AWS and Azure. Reduced deployment time by 70%.",
      tags: ["Ansible", "AWS", "Azure", "IaC"],
      link: "#"
    },
    {
      title: "E-commerce Platform",
      description: "Built a full-stack e-commerce platform using Next.js, Django REST framework, and MongoDB. Implemented real-time inventory tracking and payment processing.",
      tags: ["Next.js", "Django", "MongoDB", "REST API"],
      link: "#"
    },
    {
      title: "DevOps Pipeline",
      description: "Created CI/CD pipelines using Azure DevOps for automated testing and deployment. Integrated with multiple cloud services and monitoring tools.",
      tags: ["Azure DevOps", "CI/CD", "Docker", "Kubernetes"],
      link: "#"
    }
  ];

  const skills = {
    "Frontend": ["Next.js", "React", "TypeScript", "Tailwind CSS"],
    "Backend": ["Django", "Python", "REST APIs", "GraphQL"],
    "Database": ["MongoDB", "PostgreSQL", "Redis"],
    "Cloud & DevOps": ["AWS", "Azure", "Ansible", "Docker", "Kubernetes"]
  };

  return (
    <div className="min-h-screen bg-gray-50">
      {/* Header/Hero Section */}
      <header className="bg-gradient-to-r from-blue-600 to-indigo-700 text-white py-20">
        <div className="container mx-auto px-6">
          <h1 className="text-4xl font-bold mb-4">Full Stack Developer</h1>
          <p className="text-xl mb-6">Specializing in Cloud Infrastructure & Modern Web Development</p>
          <div className="flex space-x-4">
            <a href="#" className="p-2 hover:text-blue-200"><Github /></a>
            <a href="#" className="p-2 hover:text-blue-200"><Linkedin /></a>
            <a href="#" className="p-2 hover:text-blue-200"><Mail /></a>
          </div>
        </div>
      </header>

      {/* Main Content */}
      <main className="container mx-auto px-6 py-12">
        {/* Navigation Tabs */}
        <div className="flex space-x-4 mb-8">
          <button
            onClick={() => setActiveTab('projects')}
            className={`px-4 py-2 rounded-lg ${
              activeTab === 'projects' 
                ? 'bg-blue-600 text-white' 
                : 'bg-gray-200 hover:bg-gray-300'
            }`}
          >
            Projects
          </button>
          <button
            onClick={() => setActiveTab('skills')}
            className={`px-4 py-2 rounded-lg ${
              activeTab === 'skills' 
                ? 'bg-blue-600 text-white' 
                : 'bg-gray-200 hover:bg-gray-300'
            }`}
          >
            Skills
          </button>
        </div>

        {/* Projects Section */}
        {activeTab === 'projects' && (
          <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
            {projects.map((project, index) => (
              <div key={index} className="bg-white rounded-lg shadow-md p-6 hover:shadow-lg transition-shadow">
                <h3 className="text-xl font-semibold mb-3">{project.title}</h3>
                <p className="text-gray-600 mb-4">{project.description}</p>
                <div className="flex flex-wrap gap-2 mb-4">
                  {project.tags.map((tag, tagIndex) => (
                    <span key={tagIndex} className="bg-blue-100 text-blue-800 text-sm px-3 py-1 rounded-full">
                      {tag}
                    </span>
                  ))}
                </div>
                <a href={project.link} className="flex items-center text-blue-600 hover:text-blue-800">
                  View Project <ExternalLink className="ml-2 h-4 w-4" />
                </a>
              </div>
            ))}
          </div>
        )}

        {/* Skills Section */}
        {activeTab === 'skills' && (
          <div className="grid grid-cols-1 md:grid-cols-2 gap-6">
            {Object.entries(skills).map(([category, skillList]) => (
              <div key={category} className="bg-white rounded-lg shadow-md p-6">
                <h3 className="text-xl font-semibold mb-4 flex items-center">
                  {category === 'Frontend' && <Code className="mr-2" />}
                  {category === 'Backend' && <Server className="mr-2" />}
                  {category === 'Database' && <Database className="mr-2" />}
                  {category === 'Cloud & DevOps' && <Cloud className="mr-2" />}
                  {category}
                </h3>
                <div className="flex flex-wrap gap-2">
                  {skillList.map((skill, index) => (
                    <span key={index} className="bg-gray-100 text-gray-800 px-3 py-1 rounded-full">
                      {skill}
                    </span>
                  ))}
                </div>
              </div>
            ))}
          </div>
        )}
      </main>
    </div>
  );
};

export default Portfolio;